---
title: 编写Check_MK插件

date: 2018-05-19 8:26

tags:
- Check_MK
- Check_MK_plugin

categories:
- Check_MK

---

### 编写check_mk的插件

**1.** 前提条件是在客户端安装上check_mk_agent.

**2.** 在客户端创建插件

- [ ] 在该目录(/usr/lib/check_mk_agent/plugins)下添加自己的监控脚本

<!-- more -->

```
[liuyang@localhost plugins]$ cat showdisk
#!/usr/bin/env python

import subprocess

def get_disk_space(user):
        run_watch = subprocess.Popen("du -s /home/%s " % user,
                shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
        ret, err_msg = run_watch.communicate()
        return ret

if "__main__" == __name__:
        welcome_str = "<<<showdisk>>>\n"
        user_list = ["liuyang", "perry", "jessica", "xiaodw"]
        for user in user_list:
                disk_space = get_disk_space(user)
                welcome_str += user + "\t\t" + disk_space.split("\t")[0] + "\n"
        print welcome_str

```

- [ ] 上述命令搜集的是在该机器上所有用户的磁盘空间占用率。显示结果如下：

```
[root@localhost plugins]# ./showdisk
<<<showdisk>>>
liuyang         3771980
perry           6134268
jessica         2684096
xiaodw          7578872
```

**3.** 在监控端创建插件

- [ ] 首先确认上面的监控脚本是否成功

```
OMD[lxce@7f3c49fe22bf]:~$ cmk -d hostip | grep -A 3 showdisk
<<<showdisk>>>
liuyang         3771980
perry           6134268
```

**4.** 在该目录(/omd/sites/lxce/share/check_mk/checks)添加脚本showdisk.注意: 该脚本名字需要与上面给的<<<showdisk>>>保持一致。

```
OMD[lxce@7f3c49fe22bf]:~/share/check_mk/checks$ cat showdisk
#!/usr/bin/python
# -*- encoding: utf-8; py-indent-offset: 4 -*-

# 对于showdisk_default_values是对该检查阀值的定义，在该处定义之后可以在配置/omd/sites/lxce/var/check_mk/autochecks/redhat68.mk中更容易的修改, 该处配置在改变yield第二个参数后，需要手动修改
showdisk_default_values = (20000, 30000)


def inventory_showdisk(info): # info的内容即为上面showdisk所给出的数据。
    for line in info:
        name = line[0]
        size = line[1]

        # 通过该次过滤可以把想要的数据设置为要监控的项，每个yield都会成为一个check的servie，可以在wato中设置监控或者不监控。
        if name == "liuyang":
            yield name, "showdisk_default_values"


def check_showdisk(item, params, info): #item还未搞清楚，params即为上面设置的showdisk_default_values,可以通过该变量更容易的定义阀值，info和上面的一样是客户端的显示数据。
    use_disk = ""
    warn, crit = params
    for line in info:
        name = line[0]
        size = line[1]
        if name == "liuyang":
           use_disk = size
           break

    # 在此处因为需要和阀值进行比较，所以需要转换为int类型
    use_num = int(use_disk)
    # prefdata数据可以产生pnp4nagios图表，有几组数据，产出几个图表。
    prefdata = [ ("liuyang disk", use_num, warn, crit), ("my show", 240, 300, 400, 0, 500) ]
    # 0 - ok, 1 - warn, 2 - crit, 3 - unknow
    if use_num > warn:
        return 2, "liuyang have used disk: %s" % use_num, prefdata
    else:
        return 0, "liuyang have used disk: %s" % use_num, prefdata


check_info["showdisk"] = {
    'check_function':            check_showdisk,
    'inventory_function':        inventory_showdisk,
    'service_description':       '%s use disk', # 显示为service的名称
    'has_perfdata':              True, # 此处为显示pnp4nagios图表
}
```

**5.** 写好之后确定是否生效。

```
OMD[lxce@7f3c49fe22bf]:~/share/check_mk/checks$ cmk -nv miaoli_rh68
Check_mk version 1.2.8p20
liuyang use disk     OK - liuyang have used disk: 3771980
OK - Agent version 1.2.8p20, execution time 0.6 sec|execution_time=0.636 user_time=0.330 system_time=0.150 children_user_time=0.000 children_system_time=0.000
```

**6.** 在check_mk网页中查看。

- [ ] WATO -> Hosts -> Folder -> 选择对应机器的Edit the service -> 在available中查看是否有刚才添加的service -> 手动选中添加到监控列表中

<!--blog-->