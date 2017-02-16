## popen & system

* 相同点: Popen 和 system 都可以执行外部命令

* 不同点: 

> ** 1. ** popen 总是和 pclose一起出现使用的。popen创建一个管道，通过fork来创建一个子进程，然后执行command。其返回值在标准io流中，由于是在管道中，因此数据是单向的，command只能产生输出stdout或者是输入stdin, 所以type的值只能是两个,'w' 或者'r'.r表示command从管道中读取数据，而w表示command表示stdout输出到管道中。
