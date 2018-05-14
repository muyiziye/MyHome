---
title: 使用docker 配置Check_MK

date: 2018-05-13 18:52

tags:
- Docker
- Check_MK

categories:
- docker

---

### 使用docker 安装Check_MK

---

**1.** 搜索check_mk的docker镜像

- [ ]  docker search omd

**2.** 下载omd镜像

- [ ] docker pull consol/omd-labs-ubuntu

**3.** 运行该omd镜像

- [ ] docker run -it -p 5000:5000 -p 80:8080 -v /omd/sites/:/omd/sites/ 71927b4c83dd /bin/bash

<!-- more -->

**4.** 创建相应的site

- [ ] omd create lxce

**5.** 修改/omd/sites/lxce/etc/apache/apache.conf，监听8080端口，Listen 8080

**6.** 修改site.cfg配置

- [ ] vim /omd/sites/lxce/etc/omd/site.conf

- [ ] 修改CONFIG_CORE='naemon' 为 nagios

- [ ] 修改CONFIG_DEFAULT_GUI='thruk' 为nagios

**7.** 重新定相core的软链接

- [ ] cd /omd/sites/lxce/etc/init.d/ 

- [ ] rm core, ln -s nagios core

- [ ] 否则在使用cmk -R的时候会出现错误

**7.** 启动该site

- [ ] su - lxce, omd start

- [ ] 或者直接运行/root目录下的start.sh脚本启动，用这个脚本启动的话是启动demo sites

**8.** 此时可以通过外部网络连接Check_MK, https://xx.xx.xx.xx:80/lxce/check_mk, 用户omdamin，密码omd



### 注意事项：

**1.** 该docker退出之后会自动关闭site

**2.** 网址输入为https://xx.xx.xx.xx:80/lxce的话，会进入另外一个nagios的网站

**3.** 必须输入完整的地址https://xx.xx.xx.xx:80/lxce/check_mk，才可以进入

**4.** 直接使用默认的vim /omd/sites/demo/etc/omd/site.conf配置的话，会使得livestatus不能正常工作。

**5.** 在docker里面使用cmk -R的时候出现问题，因为/omd/sites/lxce/etc/init.d/core软链接指向的是naemon，重新定相到nagios就好了。

**6.** 改为nagios启动时，需要删除~/etc/apache/conf.d/nagios_disable.conf文件。


<!--blog-->