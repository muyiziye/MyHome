### DockerFile 

---

**1.** FROM 命令

- FROM指令指定了新的镜像是以哪一个镜像为基础开始构建的。

**2.** ENTRYPOINT命令

- 该指令设置了从该镜像创建的容器启动时需要执行的命令。

**3.** CMD命令

- 使用该命令的优点是可以在启动容器的时候通过在docker run命令后面指定新的CMD参数来覆盖Dockerfile文件中设置的内容

> 对于CMD 和 ENTRYPOINT两者，CMD可以通过docker run后面的参数来覆盖。而ENTRYPOINT的话只能通过docker run的--entrypoint参数来覆盖了。

**4.** RUN命令

- RUN命令允许在构建镜像的时候执行指定的shell命令。

**5.** EXPOSE命令

- EXPOSE指令将应用程序监听的端口暴露给外部。

**6.** ADD命令

- ADD指令将应用程序复制到容器内的系统文件上。

---

### 开始构建docker镜像

**1.** 在完成了Dockerfile之后可以使用docker build . 来进行构建

**2.** 直接使用上面的命令来构建的话，没有仓库名和标签信息，可以通过docker build -t参数来为仓库设置名字和标签docker build -t testdocker:hello .

**3.** 在构建过程中，Docker会将Dockerfile所在文件夹下的目录复制到构建环境中，使用.dockerignore文件可以将指定的文件或者是文件夹在镜像构建时从文件复制列表中排除。

**4.** 最大程度的减少镜像的层数。