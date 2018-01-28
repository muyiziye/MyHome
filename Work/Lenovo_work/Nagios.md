### Nagios 安装以及实践

**1.** 参考文档

> http://www.cnblogs.com/mchina/archive/2013/02/20/2883404.html

---

**question** 

**1.** 在安装apach的时候出现问题：

> checking for APR... no

> solutions: 安装apr包， 参考 http://blog.chinaunix.net/uid-26986973-id-3246235.html

**2.** 在安装apt-util-1.6.0的时候出现xml/apr_xml.c:35:19: error: expat.h: No such file or directory

> 使用命令yum install expat-devel来安装expat-devel包

> 查看资料：http://www.codes51.com/itwd/4401668.html

**3.** 在ubuntu上安装的nagios使用的账号为nagiosadmin 密码abc-123

---

### nrpe

**1.** 配置添加新的节点

>  在被管理节点的/usr/local/nagios/libexe里面添加命令脚本， 添加权限等。(Lenovo_power_dissipation, Lenovo_SSD_Remain_life) 

>  在被管节点的/usr/local/nagios/etc/nrpe.cfg里面添加对该命令的定义。

>  重启被管理节点的nrpe命令：(首先需要kill掉原来的nrpe进程)/usr/local/nagios/bin/nrpe -c /usr/local/nagios/etc/nrpe.cfg -d

>  在管理节点的/usr/local/nagios/etc/objects/linhost.cfg中添加对应的机器和命令。

>  重启动下管理节点的nagios：/etc/init.d/nagios restart

### snmp

> 当前只是使用了docker安装了snmp的方式的nagios，用户名nagiosadmin 密码nagios

**1.** 在安装snmp中遇到问题

---

> snmpwalk -c public -v 2c localhost sysName.0 

> 此命令运行之后出现sysName.0: Unknown Object Identifier (Sub-id not found: (top) -> sysName)

> 修改方法：修改/etc/snmp/snmp.conf 注释掉mibs： 后重启服务即可。

> 之后即可获取数据：SNMPv2-MIB::sysName.0 = STRING: Kakao-ubuntu16043

---

> 安装snmp的plugin的时候./configure 提示没有找到net-snmp-config文件

> 对于ubuntu来说 sudo apt-get install snmpd libsnmp-dev即可解决相应问题。

---

### snmp的server端安装

- a. 首先要安装snmpd和libsnmp-dev

- b. 安装好之后，需要定义command，在/usr/local/nagios/etc/object/commands.cfg中定义该命令。

- c. 在lin_snmp.cfg文件中添加check_snmp的命令。

- d. 在nagios.cfg文件中添加上面的文件。

- e. 检查配置文件：/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

- f. service nagios restart 重启nagios服务

- g. 使用command ./check_snmp_storage -H 10.240.204.243 -C public -m ^Swap -w 80 -c 90 -f 来测试其他的机器是否work

- h. 使用命令snmpwalk  -v3 -l authPriv -u USERID -a SHA -A PASSW0RD -x DES -X Passw0rd  -t 10  10.240.193.148 1.3.6.1.4.1.19046.11.1.1.3.1.0 来获取相应的fan的个数。

---

### 创建分组

**方式 1 创建service分组**

- A. 打开文件 /usr/local/nagios/etc/objects/lin_snmp.cfg

- B. 添加对分组的定义

<pre>
define servicegroup{
    servicegroup_name     SNMP-XCC-Ctrl
    alias                 SNMP XCC
}
</pre>

- C. 添加对机器的特定命令的定义

<pre>
define service{
    use                      generic-service  # 这个貌似是默认的设置，开起来都是这样的
    host_name                Lenovo_1
    service_description      Lenovo_purley_machine
    check_command            my_command!ARG1!ARG2!ARG3
    servicegroups            SNMP-XCC-Ctrl    # 在这里就是设置把Lenovo_1这台机器的my_command 命令
}
</pre>

**方式 2 创建host分组和创建service分组**

* A. 创建host分组

打开文件lin_snmp.cfg

<pre>
define hostgroup{
    hostgroup_name          group1 #组名
    alias                   Lenovo #别名
    members                 主机名1，主机名2 #组中成员的主机名
}
</pre> 

* B. 创建service分组

<pre>
definde servicegroup{
    servicegroup_name        disk_check  #服务组名
    alias                    disk
    members                  成员1，服务1，成员2，服务2
}
</pre>

* C. 创建所有分组内机器都使用的命令

<pre>
define service {
    hostgroup_name           disk_check  # 服务组名
    service_description      disk
    check_command            check_disk
    use                      generice-service
    notification_interval    0 ; set > 0 if you want to be renotified # 该处还不太清楚使用方式
}
</pre>

* D. 上面两步之后都需要重启下服务service nagios restart

---

### OID for purley

**1.** Fan：  1.3.6.1.4.1.19046.11.1.1.3.2

**2.** Power Module：  .1.3.6.1.4.1.19046.11.1.1.11

**3.** Local storage：   .1.3.6.1.4.1.19046.11.1.1.13

**4.** Support process：  .1.3.6.1.4.1.19046.11.1.158

**5.** system vpd Memory：.1.3.6.1.4.1.19046.11.1.1.5.21

**6.** System health：  .1.3.6.1.4.1.19046.11.1.1.4

---

### 使用ipmitool获取数据

- Fan  ipmitool sensor list |grep "Tach"
