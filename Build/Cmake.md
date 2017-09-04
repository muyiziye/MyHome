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

   > MESSAGE([SEND_ERROR | STATUS | FATAL_ERROR] “message to display” …)

   > 向终端输出用户定义的信息或变量的值

   > SEND_ERROR, 产生错误,生成过程被跳过

   > STATUS, 输出前缀为--的信息

   > FATAL_ERROR, 立即终止所有cmake过程

* include_directories (追加标志 头文件路径)

   > INCLUDE_DIRECTORIES([AFTER|BEFORE] [SYSTEM] dir1 dir2 ...)

   > 向工程添加多个特定的头文件搜索路径，路径之间用空格分隔，如果路径包含空格，可以使用双引号将它括起来。默认的行为是追加到当前头文件搜索路径的后面。

   > 有如下两种方式可以控制搜索路径添加的位置：CMAKE_INCLUDE_DIRECTORIES_BEFORE,通过SET这个cmake变量为on,可以将添加的头文件搜索路径放在已有路径的前面. 通过AFTER或BEFORE参数,也可以控制是追加还是置前

   > INCLUDE_DIRECTORIES类似gcc中的编译参数“-I”，指定编译过程中编译器搜索头文件的路径。当项目需要的头文件不在系统默认的搜索路径时，需要指定该路径。

* string 命令

   > string 通过正则表达式来获取相应的变量值。

* add_definitions 命令

   > ADD_DEFINITIONS(-DENABLE_DEBUG-DABC)，添加编译参数

   > add_definitions( “-Wall -ansi –pedantic –g”) 或者 add_definitions(-DDEBUG)将在gcc命令行添加DEBUG宏定义，等等

* link_directories (库文件路径)

   > link_directories(directory1 directory2 ...)

   > 后面接动态链接库或静态链接库的搜索路径, 它相当于g++命令的-L选项的作用

* CONFIGURE_FILE

   > configure_file: 将一份文件拷贝到另一个位置并修改它的内容

   > configure_file(\<input\> \<output\> [COPYONLY] [ESCAPE_QUOTES] [@ONLY]) 

   > 将文件\<input\>拷贝到\<output\>然后替换文件内容中引用到的变量值,对于module来说只使用了最基本的拷贝文件的功能。

* add_subdirectory

   > ADD_SUBDIRECTORY(src_dir [binary_dir] [EXCLUDE_FROM_ALL])

   > 向当前工程添加存放源文件的子目录，并可以指定中间二进制和目标二进制的存放位置

   > EXCLUDE_FROM_ALL含义：将这个目录从编译过程中排除

   > SET(EXECUTABLE_OUTPUT_PATH${PROJECT_BINARY_DIR}/bin)更改生成的可执行文件路径

   > SET(LIBRARY_OUTPUT_PATH${PROJECT_BINARY_DIR}/lib)更改生成的库文件路径

* execute_process

   > 执行一个或多个子进程

   > execute_process(COMMAND <cmd1>[args1...]]
                  [COMMAND <cmd2>[args2...] [...]]
                  [WORKING_DIRECTORY<directory>]
                  [TIMEOUT<seconds>]
                  [RESULT_VARIABLE<variable>]
                  [OUTPUT_VARIABLE <variable>]
                  [ERROR_VARIABLE<variable>]
                  [INPUT_FILE<file>]
                  [OUTPUT_FILE<file>]
                  [ERROR_FILE<file>]
                  [OUTPUT_QUIET]
                  [ERROR_QUIET]
                 [OUTPUT_STRIP_TRAILING_WHITESPACE]
                 [ERROR_STRIP_TRAILING_WHITESPACE])

   > 按指定的先后顺序运行一个或多个命令，每个进程的输出通过管道连接作为下一个进程的输入。所有的进程使用单个的标准错误输出管道。如果指定了WORKING_DIRECTORY，则指定的目录将作为子进程当前的工作目录。如果指定了TIMEOUT值，则如果在指定的时间内（以秒为单位计算，允许有小数位）子进程执行仍未完成，则将会被中断。如果指定了RESULT_VARIABLE变量，则最后命令执行的结果将保存在该变量中，它是最后一个子进程执行完后的返回值或描述某种错误信息的字符串。如果指定了OUTPUT_VARIABLE或ERROR_VARIABLE变量，则该变量会分别保存标准输出和标准错误输出的内容。如果指定的变量是同一个，则输出会按产生的先后顺序保存在该变量中。如果指定了INPUT_FILE，　OUTPUT_FILE或ERROR_FILE等文件名，则它们会分别与第一个子进程的标准输入，最后一个子进程的标准输出以及所有子进程的标准错误输出相关联。如果指定了OUTPUT_QUIET或ERROR_QUIET，则会忽略标准输出和错误输出。如果在同一管道中同时指定了多个OUTPUT_*或ERROR_*选项，则优先级顺序是未知的（应避免这种情况）。如果未指定任何OUTPUT_*或ERROR_*选项，则命令CMake所在进程共享输出管道。

* INSTALL 命令解析

   >  INSTALL(TARGETS hellohello_static LIBRARY DESTINATION lib ARCHIVE DESTINATION lib)

   > INSTALL(FILES hello.h DESTINATIONinclude/hello)

   > 注意，静态库要使用ARCHIVE关键字

   > cmake -DCMAKE_INSTALL_PREFIX=/usr ..[路径]

   > INSTALL(TARGETS targets...
	[ [ARCHIVE|LIBRARY|RUNTIME]
	[DESTINATION < dir >]
	[PERMISSIONS permissions...]
	[CONFIGURATIONS
	[Debug|Release|...]]
	[COMPONENT < component >]
	[OPTIONAL]
	] [...])

   > 参数中的 TARGETS 后面跟的就是我们通过 ADD_EXECUTABLE 或者 ADD_LIBRARY 定义的目标文件,可能是可执行二进制、动态库、静态库。
    DESTINATION 定义了安装的路径,如果路径以/开头,那么指的是绝对路径,这时候CMAKE_INSTALL_PREFIX 其实就无效了。如果你希望使用 CMAKE_INSTALL_PREFIX 来定义安装路径,就要写成相对路径,即不要以/开头,那么安装后的路径就是${CMAKE_INSTALL_PREFIX} /< destination 定义的路径>
    你不需要关心 TARGETS 具体生成的路径,只需要写上 TARGETS 名称就可以了。

   > INSTALL(PROGRAMS files... DESTINATION < dir >
	[PERMISSIONS permissions...]
	[CONFIGURATIONS [Debug|Release|...]]
	[COMPONENT < component >]
	[RENAME < name >] [OPTIONAL])

   > 跟上面的 FILES 指令使用方法一样,唯一的不同是安装后权限为OWNER_EXECUTE, GROUP_EXECUTE, 和 WORLD_EXECUTE,即 755 权限目录的安装

   > INSTALL(DIRECTORY dirs... DESTINATION < dir >
	[FILE_PERMISSIONS permissions...]
	[DIRECTORY_PERMISSIONS permissions...]
	[USE_SOURCE_PERMISSIONS]
	[CONFIGURATIONS [Debug|Release|...]]
	[COMPONENT < component >]
	[ [PATTERN < pattern > | REGEX < regex >]
	[EXCLUDE] [PERMISSIONS permissions...]] [...])

   > DIRECTORY 后面连接的是所在 Source 目录的相对路径,但务必注意:abc 和 abc/有很大的区别。如果目录名不以/结尾,那么这个目录将被安装为目标路径下的 abc,如果目录名以/结尾,代表将这个目录中的内容安装到目标路径,但不包括这个目录本身

* target_link_libraries 命令解析

   > 