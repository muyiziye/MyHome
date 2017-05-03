### 怎么编译libcurl

**1.** 下载libcurl源码：https://curl.haxx.se/download/?C=M;O=A

**2.** 安装，指定安装目录为/usr/local/curl

> ./configure --prefix=/usr/local/curl

**3.** 此处应该配置Makefile文件

**4.** make进行编译，sudo make install进行安装 