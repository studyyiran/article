第一次听说mongo的时候，还是17年刚成为前端菜鸟的时候。现在我也把他学起来了。做个简单的，不专业的学习笔记，以下内容肯定有误。后续我会根据所学继续修改。

### 连接数据库
```javascript
```

```javascript
mongoose.connect(url, option, callback)
```

option有一些常用的参数。例如useNewUrlParse，readyAsync等等

链接数据库，返回的是一个promise。但是你不需要await。他会等待你然后ok的


### schema 和model
Schema我理解到，他和TS的interface有点像

model，我觉得有点像一个类装饰器，通过传入schema，返回一个构造函数
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
