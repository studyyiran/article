第一次听说mongo的时候，还是17年刚成为前端菜鸟的时候。现在我也把他学起来了。做个简单的，不专业的学习笔记，以下内容肯定有误。后续我会根据所学继续修改。

一些晦涩的概念
documents

一些晦涩的问题
populate为什么可以通过一个字符串就定位到？
它里面封装了mongo的查询。

### 连接数据库
```javascript
```

```javascript
mongoose.connect(url, option, callback)
```

option有一些常用的参数。例如useNewUrlParse，readyAsync等等

链接数据库，返回的是一个promise。但是你不需要await。他会等待你然后ok的。
这个promise的返回我查过了。他是一个callback和promise二选一的。

url的含义是：
protocal + hostnameIp + port +dbName

1. 他是一个promise返回
2. 他不需要wait
3. option


### 几个关系
Schema
他是用于验证

schemaTypes
里面的一些特殊的


## Model
他的大小写规则（mongoose通过他的名字来。）

他可以通过new + save和create的方法

Document
他有实例方法，每个documents都有实例方法
documents好像不能map，或者[...]

查找document可以使用findOne，findbyId


Documents 是model的实例，通过ModelName.create或者new出来
schema 是model的验证对象。


### schema 和model
Schema我理解到，他和TS的interface有点像

model，我觉得有点像一个类装饰器，通过传入schema，返回一个构造函数(models是从Schema编译来的构造函数。)
```javascript
// 生成
const studentModel = mongoose.model('modelname', Schema)

const student1 = new studentModel();
student1.save()
```



### mongoose document
上面除了返回数据对象之外，还暴露了很多的方法，用于CRUD和操作.
例如
```javascript
const studentOne = studentModel.findById(123);
studentOne.name = 'student123'
studentOne.save();
```



一些问题
我更新schema是不是会改变version呢？
我有的时候会遇到字段的覆盖问题。就是我的新字段上不去