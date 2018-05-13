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

**6.** 启动该site，su - lxce, omd start

**7.** 此时可以通过外部网络连接Check_MK, https://xx.xx.xx.xx:80/lxce/check_mk, 用户omdamin，密码omd

### 注意事项：

**1.** 该docker退出之后会自动关闭site

**2.** 网址输入为https://xx.xx.xx.xx:80/lxce的话，会进入另外一个nagios的网站

**3.** 必须输入完整的地址https://xx.xx.xx.xx:80/lxce/check_mk，才可以进入

<!--blog-->