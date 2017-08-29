## CMake 学习文档

**因为在项目中有使用CMake的地方，现对其进行整理**

**现以modularization/CMakeLists.txt为例**

* project (projectname) 

   > 该句是设定project的名字，该条命令会自动生成两个变量 \<projectname\>_BINARY_DIR(二进制文件保存路径) \<projectname\>_SOURCE_DIR（源代码路径）同时cmake系统也同时预创建两个变量PROJECT_BINARY_DIR和PROJECT_SOURCE_DIR,两者相同，这四个变量指向的路径都是该camkelist文件所在的路径。

   > 对于module项目，project (XModule) 这个命令也就是定义了两个变量 XModule_BINARY_DIR和XModule_SOURCE_DIR与PROJECT_BINARY_DIR和PROJECT_SOURCE_DIR

* cmake_minimum_required (VERSION 2.8)

   > 该句是对cmake最低版本进行要求

* set (CMAKE_MODULE_PATH /home/)

   > set (变量名 变量值)

* include ()

   > include的作用是用来载入cmakelists.txt文件，或者是载入预定义的Cmake模块。

   > include (file [optional]) 或者 include (module [optional])

   > 说明：optional的作用是即使文件不存在也不会报错， 你可以指定载入一个文件，如果定义的是一个模块，那么将在CMAKE_MODULE_PATH中搜
索这个模块并载入。载入的内容将在处理到 INCLUDE 语句时直接执行。

* file 命令

   > file命令有很多，在此仅以module给出的file(WRITE filename "message")为例，该命令WRITE选项将会写一条消息到名为filename的文件中。如果文件已经存在，该命令会覆盖已有的文件；如果文件不存在，它将创建该文件。

* if 语句

   <pre>
if(WIN32) 
# do something for win32 
else() 
# do something for not win32 
endif(WIN32)
   </pre>

   > 或者

   <pre>
if(WIN32)
# do something for win32
elseif(UNIX)
# do something for unix
elseif(APPLE)
# do somethong for apple
endif(WIN32)
   </pre>

* message 命令的使用

