## popen & system

* 相同点: Popen 和 system 都可以执行外部命令

* 不同点: 

** popen 总是和 pclose一起出现使用的。popen创建一个管道，通过fork来创建一个子进程，然后执行command。其返回值在标准