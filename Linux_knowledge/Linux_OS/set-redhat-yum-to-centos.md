---
title: 修改redhat6.8的yum源为centos6.8的

date: 2018-05-19 8:34

tags:
- redhat6.8
- yum

categories:
- redhat6.8
- yum

---

### 修改redhat6.8的yum源为centos的yum源

**1.** 检查redhat6.8是否安装了yum源

- rpm -qa | grep yum

**2.** 删除这些自带的yum源

- rpm -qa | grep yum | xargs rpm -e --nodeps 

- 上述命令不检查依赖关系直接删除rpm包

<!-- more -->

**3.** 下载最新的centos6.8的包

- wget http://mirrors.163.com/centos/6/os/x86_64/Packages/yum-3.2.29-81.el6.centos.noarch.rpm

- wget http://mirrors.163.com/centos/6/os/x86_64/Packages/yum-metadata-parser-1.1.2-16.el6.i686.rpm

- wget http://mirrors.163.com/centos/6/os/x86_64/Packages/yum-plugin-fastestmirror-1.1.30-40.el6.noarch.rpm

- 注意在这里需要下载对应的i386或者64的版本。

**4.** 安装依赖包

- rpm -ivh yum-3.2.29-81.el6.centos.noarch.rpm yum-metadata-parser-1.1.2-16.el6.x86_64.rpm yum-plugin-fastestmirror-1.1.30-40.el6.noarch.rpm

- 注意，此时需要三个rpm一起安装，因为其rpm包直接有相互依赖。（具体我没试验）

**5.** 更新yum源

- cd /etc/yum.repos.d/

- wget http://mirrors.163.com/.help/CentOS6-Base-163.repo

- 修改上面文件中$releasever 该为6，在vim中使用命令 :1,$s/$releasever/6/g

- mv mv redhat.repo  rhel-source.repo.bak

-  mv CentOS6-Base-163.repo  rhel-source.repo

**6.** 清除原有缓存

- yum clean all

- yum makecache

**7.** 更新

- yum update

<!--blog-->