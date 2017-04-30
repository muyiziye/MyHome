### 在Ubuntu14.04上创建Docker

**1.** 必须要求ubuntu内核的版本号不低于3.10，之前的版本缺少docker所需要的容器，有bug。当前机器版本uname -r 显示为3.13.0

**2.** 使用root权限登录，更新apt源，apt-get update.确保apt使用https协议，并且安装ca认证 apt-get install apt-transport-https ca-certificates

**3.** 