### DockerFile 

---

**1.** FROM 命令

- FROM指令指定了新的镜像是以哪一个镜像为基础开始构建的。

**2.** ENTRYPOINT命令

- 该指令设置了从该镜像创建的容器启动时需要执行的命令。

---

**1.** 在完成了Dockerfile之后可以使用docker build . 来进行构建