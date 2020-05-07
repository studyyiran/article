antd form
所有优雅的计算机,都有强烈的层次感,层次让我们进行各个层次的操作和注入.
但是,如果需要跨层次掌握一连串的概念,就非常非常考验人了.
恰好在前端领域,一个组件的跨层次设计是非常常见的,因为他的业务需求的确足够复杂.
例如class的层次还有form的层次.而且他们的设计往往还有冗余性,这就非常灾难了.


Form层面上有什么呢?
1)布局layout
2)onSubmit
3)hideRequireTag
这个form他就是做了form该做的事情.全局性质的样式,回调等.

> onSubmit是什么时候触发的呢？我觉得应该是，
>用户点击提交以后，通过了检测，然后触发的把。


首先在v3里面，form是由Form.create创建的。他有两个参数
一个是option，这个是传入了obj，是个简单的函数调用。
然后是Component，这是一个hoc，或者更准确，是一个装饰器。因为返回的Component被config装饰了。



create
Form.create(option)(CustomizedForm);
这也是一个decorator(也就是,他吸纳一个config),然后是一个hoc(传入Component 得到Component),但是被注入了一些方法.

option包括
onFieldsChange
onValuesChange
上面这两个方法,都是在表单发生变更的时候,触发回调.onFieldsChange结构相同,但是会有更多关于表单报错的信息

这些是,包装提需要关心的一些回调.需要进行注入的一些外部调用方法.

ref  wrappedComponentRef
wrappedComponentRef={(form) => this.form = form}
这个封装将内部的ref告知外面,从而可以获取内部的所有信息,是一个非常关键的设计.
为什么他比要呢?因为,React组件,其实缺少从外部调用内部props方法,获取内部数据的办法.
ref破坏了封装性,但是增加了灵活性.

props里面有什么呢?
getFieldDecorator  又是一个包装体.
getFieldsValue  查
setFields  改
resetFields ? 删?
validateFields 验证.
使用这些的前提都是,被getFieldDecorator 合理包装过.
为什么呢?因为,上层的包装,让我们获得了注入的方法.再次的包装,让我们能够接管onChange value等方法.


在getField层次,有这么几个关键的因素.
1)他外面有一个form.item用于包装.他可以渲染
label
总体来说,他掌管,每一个表单的行的样式相关的内容.


2.getDecoratorField(id, option)(<Input>)
他前面仍然是装饰器,后面嘛.也是一个高阶,传入一个jsx,返回一个jsx,被注入了一些表单的回调和监听.

1)id
2)option


option有.
initialValue
trigger 收集节点的触发实际
validateTrigger 检验的阐发实际
validateFirst
rules

rules是一个数组,一次校验包括
{
    required,
    type,
    message,
     validator
}
这块都是校验相关的.这块应该是结合了一些asyncValid的方法.
validator用于自定义校验.
他的函数是rules valus callback.其中,
values用于获得当前的数据,callback记住这是一个异步方法,可以callback的error用string.



其余平行方法

validateFields检测表单区域.
他是一个函数返回(errors,values),他常常在onSubmit调用,通过判断errors决定是否使用values的值

setField.设置表单区域.
他是一个函数,类似于setSttate 
{
    id: {
        value:
        errors: [new Error]
    }
}

