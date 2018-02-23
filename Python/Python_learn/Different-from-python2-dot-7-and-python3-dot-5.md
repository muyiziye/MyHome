### python2.7 and python3.5 

---

- **subprocess**

    在python2.7和python3.5中，subprocess模块的communicate有所不同，python2.7返回一个元组(stdout, stderr); 但是python3.5返回bytes或者当universal_newlines为true的时候返回两个string组成的元组。

- **haskey**

    python2.7字典查询key使用的是if dick.haskey(key1),但是在python3.5中删除了该方法，if key1 in dict: