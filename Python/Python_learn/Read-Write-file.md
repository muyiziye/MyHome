## python读写文件

---

### 1. open函数的基本介绍

* 用于打开一个文件，返回file对象。

* 方法: 

  ```
  f = open(name[, mode[, buffering]])
  ```

* name 为打开文件的名字。mode可以为读，写，追加。默认不写为只读r, 加上b为二进制方式的读取通常处理图片和音乐等。

### 2. 读取文件的n种方式

**A.** f.read([size]) 读取指定的字节数，未给定或为负数则全部读取，返回字符串

**B.** f.readline([size]) 读取整行，其中包括\n 字符，返回字符串。 通常使用方法为（暂时没有找到其和with一起使用的方法）

  ```
  f = open(file_name):
  for line in f.readline():
     print line
  f.close()
  ```

**C.** f.readlines([size]) 读取全部文件并且返回列表，size设置一次读取多少字节，但其仍然是按照整行处理。
  
  ```
  with open(file_name, 'r') as f:
    for line in f.readlines():
        print line
  ```

**D.** 或者不用上面三种, 因为open的返回值直接就是可迭代对象

  ```
  with open(file_name) as f:
    for line in f:
      print line
  ```

### 3. 写入文件

