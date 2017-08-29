## CMake 学习文档

**因为在项目中有使用CMake的地方，现对其进行整理**

**现以modularization/CMakeLists.txt为例**

* 1. project (projectname) 

   > 该句是设定project的名字，该条命令会自动生成两个变量 \<projectname\>_BINARY_DIR(二进制文件保存路径) \<projectname\>_SOURCE_DIR（源代码路径）同时cmake系统也同时预创建两个变量PROJECT_BINARY_DIR和PROJECT_SOURCE_DIR,两者相同，这四个变量指向的路径都是该camkelist文件所在的路径。

   > 对于module项目，project (XModule) 这个命令也就是定义了两个变量 XModule_BINARY_DIR和XModule_SOURCE_DIR与PROJECT_BINARY_DIR和PROJECT_SOURCE_DIR


