### 在Ubuntu14.04上创建Docker

**1.** 必须要求ubuntu内核的版本号不低于3.10，之前的版本缺少docker所需要的容器，有bug。当前机器版本uname -r 显示为3.13.0

**2.** 使用root权限登录，更新apt源，apt-get update.确保apt使用https协议，并且安装ca认证 apt-get install apt-transport-https ca-certificates

**3.** 添加新的GPGkey apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

**4.** 打开或者创建文件：/etc/apt/sources.list.d/docker.list，添加 deb https://apt.dockerproject.org/repo ubuntu-trusty main （具体的添加内容对于不同ubuntu版本不同）

**5.** 更新apt包 apt-get update

**6.** 清除旧的repo if it exists， apt-get purge lxc-docker

**7.** 确保 APT 是从正确的代码库拉取下来的 apt-cache policy docker-engine

**8.** ubuntu安装的先决条件apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual（针对Ubuntu Trusty, Wily, and Xenial, 推荐安装 the linux-image-extra-* 内核包.  linux-image-extra-* 包允许你使用 aufs存储驱动.为了安装 linux-image-extra-* ）

**9.** 安装docker，apt-get install docker-engine

**10.** 使用docker， docker run hello-world