### 创建Docker私有registry

---

**1.** 拉去registry镜像

- 命令：docker pull registry:2

**2.** 以守护进程的方式启动容器

- docker run -d -p 5000:5000 registry

**3.** 查看该容器是否正常启动

- curl -i http://localhost:5000/v2/

### **由于目前不需要该功能，文档暂时搁浅**