### 在编译onecli的时候遇到的问题

**1.** 没有这个文件/lib/ld-linux.so.2

> yum install glibc -y, 但是在yum源不能很好的使用，所以下面开始更换源,此时也可以直接使用rpm包安装rpm -ivh glibc-2.24-6.fc25.i686.rpm --force --nodeps，与此同时还需要安装两个包rpm-devel-4.4.2.3-37.16.37.x86_64.rpm和popt-devel-1.7-37.16.37.x86_64.rpm，对与前者，在redhat上面可能需要换成rpm-devel-4.8.0-55.el6.x86_64.rpm，因为4.4.2中会缺少#include <rpm/rpmlegacy.h>文件。

**2.** 更换yum源

> 首先需要备份系统自带的源，mv /etc/yum.repos.d/rhel-source.repo /etc/yum.repos.d/rhel-source.repo.bak；然后删除redhat自带的yum包： rpm -aq | grep yum|xargs rpm -e --nodeps；在接着下载centos的源
wget  http://mirror.centos.org/centos/7/os/x86_64/Packages/python-iniparse-0.4-9.el7.noarch.rpm
wget  http://mirror.centos.org/centos/7/os/x86_64/Packages/yum-metadata-parser-1.1.4-10.el7.x86_64.rpm
wget  http://mirror.centos.org/centos/7/os/x86_64/Packages/yum-3.4.3-118.el7.centos.noarch.rpm
wget  http://mirror.centos.org/centos/7/os/x86_64/Packages/yum-plugin-fastestmirror-1.1.31-24.el7.noarch.rpm

**3.** 保存镜像
http://blog.csdn.net/wuzhilon88/article/details/41675399