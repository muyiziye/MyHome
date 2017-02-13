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