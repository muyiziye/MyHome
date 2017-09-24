### 编译linux内核

**1.** as86和ld86找不到

> 运行apt-cache search as86 ld86 返回 bin86 - 16-bit x86 assembler and loader,由此可以知道这两个编译工具在bin86中。

> apt-get install bin86安装此命令。

**2.** 遇到boot/head.s:43: Error: unsupported instruction `mov'等一系列的head.s中的问题

> 在对应的makefile文件的gcc后面添加-m32编译即可