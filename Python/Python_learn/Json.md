## 解析Json 数据
1. 首先Json是一种轻量级的数据交换格式。
2. python处理Json的具体方法

* json.dumps()
* 该函数可以将简单数据类型转换为json格式
* 实例:
* import json 
* src_data = {"name":"Tacey","age":13,"sex":"male","interst":("Programing","Reading")}
* print json.dumps(src_data)

* json.loads()
* 该函数可以将json格式转换为python的简单数据结构
* 实例:
* json_data = json.dumps(src_data)
* print json.loads(json_data)["name"]

3. 读写json文件

* 写json文件
```
with open(json_name, "w") as dump_f:
    json.dump(json_report, dump_f, indent=4)
```

* 都json文件
```
with open(json_name, "r") as load_f:
    load_dict = json.load(load_f)
```