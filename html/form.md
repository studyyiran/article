form是表单
http://blog.shaochuancs.com/w3c-html5-input/

回调
onSubmit。提交的回调。

form上面有属性
包括
action：目标url
type：提交的格式(enctype。数据的编码类型，如application/x-www-form-urlencoded。)
method：get post
autocomplete: on off


form的局限是似乎没办法设置header


方法
submit()提交表单
reset()重置表单

input
通过name字段，来进行。
会将form下面，所有含有name的元素，都放到body里面，提交出去


label
label是用来 点击后，触发对应的input。
