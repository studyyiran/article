

## schema是什么？
Each schema maps to a MongoDB collection and defines the shape of the documents within that collection.

## collection是什么？
colleaciton是document的持有者。他的容器是db
collection  === Schema（是collection的映射。为documents提供校验服务。）(数据校验映射) -> model（提供生成documents的构造函数） -> document（model的实力，提供方法）

## _id在哪里出现
每个document都有_id
subDocument（例如arr里面的一个Schema。）似乎也会创建？（不不会。只有populate才会应该是）
对于subDocuments你可以通过设置schema的{_id: false}实现关闭id

## schemaTypes是什么？
schemaType只是描述类型的。他不是类型本身。


问题
schemaTypes究竟是什么？
model和db的关系
documents的关系。

就可以了。

{timestamps: true} 自带时间戳

required
default
unique：唯一索引
type：mongoose.Schema.Types.ObjectId;

## connection
他是一个异步操作。
我们可以凭空创建model。
但是当我么你试图生成documents实例的时候，我们会默认等待数据库的链接（因为这个操作需要数据库）
> 因为我觉得，你可以做的事情是什么？你可以生成一个对象，通过你的schema验证。
>但是当你查或者插入的时候，你首先需要，拿着model-name 去找到对应的collection。然后，你才可以搞事情。
>因此这块会挂起
>


## model
Models are fancy constructors compiled from Schema definitions.
An instance of a model is called a document.
Models are responsible for creating and reading documents from the underlying MongoDB database.

model通过这个转化为小写的名字，去从db的所有的collection中寻找到对应的。
（所以没事不要改这个名字，这个也不能重复。那就成一个变量了。而且我确信populate的时候，是填入的这个名字。而且他搜索
的db是默认的mongo链接的db）

## document
document是model的实例。


这块有两个遗留
1）如何更新
2）findById
3）会不会报错，如何报错