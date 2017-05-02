**1.** 下载相关的镜像

> 使用sudo docker search来查询相关的image， 然后使用sudo docker pull XXX 来下载所需要的image文件。

**2.** 运行相关docker

> 使用命令sudo docker run -i -t imageID /bin/bash 来启动一个container，并且开启一个terminal。如果运行中关闭了这个terminal之后，container已经在后台运行了，此时想在一次的连接该container可以使用命令 sudo docker exec containerID -it /bin/bash. 或者使用命令sudo docker attach containerID, 但是我在运行此命令的时候卡住了

**3.** 