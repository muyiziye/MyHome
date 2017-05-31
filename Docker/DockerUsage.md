**1.** 下载相关的镜像

> 使用sudo docker search来查询相关的image， 然后使用sudo docker pull XXX 来下载所需要的image文件。因为从官方Docker Hub下载非常慢，所以这里从国内的镜像站http://dockerpool.com/下载，具体命令如下：

> docker pull dl.dockerpool.com:5000/ubuntu:14.04

**2.** 运行相关docker

> 使用命令sudo docker run -i -t imageID /bin/bash 来启动一个container，并且开启一个terminal。如果运行中关闭了这个terminal之后，container已经在后台运行了，此时想在一次的连接该container可以使用命令 sudo docker exec containerID -it /bin/bash,在此环境下如果输入exit命令,那么该container仍然在后台中运行. 或者使用命令sudo docker attach containerID，输入exit命令，那么该container则会直接推出。

**3.** 制作镜像

> sudo docker commit -m "message body" old_Docker_container_ID new_Docker_Name

**4** docker run -it --privileged=true -v /root/workdir/code/:/code opensuse11-onecli-build-env sh
