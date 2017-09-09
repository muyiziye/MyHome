## 创建模块

   * 1. 我们要知道模块在什么位置，\\source\\mmi\_app\\app目录下就是各个模块，可以通过名称基本判断相关功能。

   * 2. 创建一个新的模块，首先要在上述的app目录下面建立自己的文件夹以sample为例，然后再sample文件夹下创建两个文件夹，分别是c和h，接着分别在c目录和h目录下创建sample\_main.c和sample\_main.h两个文件，并将写好的代码放进去。

   * 3. 编译APP，在APP模块创建好了之后，仍然需要将文件加入工程才能进行编译，我们可以在\\make\\app目录下找到app.mk文件，添加“MSRCPATH += 相关c文件的路径”。同时添加“MINCPATH += 相关h文件的路径”。并且在“SOURCES=”后面的一堆文件名中加上sample\_main.c。使用 make m=simulator\_main job =4 重新生成模拟器就可以了。
