## 划分，browser，server还有share
前两个仅仅是两个入口文件，差异仅仅是路由不一样。
share就是app组件。最外层就是proider -> switch -> route
前端的入口文件：
后端的入口文件：


## 路由匹配，获取目标组件，还有ssr.js
这个就是用routerConfig配合useMatch做路由匹配。找到target.
然后发起请求即可。


## 服务端发起，获得data
执行一个很简单的js，去把所有数据都异步的获取好。

> 这块我写的时候遇到障碍，就是我理解不了为什么toString无法执行类的生命周期函数。
React中的大部分函数，在服务端不会执行。

然后返回一个json，进行后续的使用。

## 服务端，用data，通过function得到view1
现在我们有了通过ssr.js获得的请求。再加上匹配到的Page，我们就可以从路由入口，将数据扔进去。

function + data = view。
我们拿到了一个静态的view。


## 后续一些操作
我们先获取了html模板，然后将view写到了app里面。
例如设定title，meta标签。不赘述


## 通过html将data传过去
在script的最后。这里面有个细节，必须放在main.js之前。不然会有问题
设定好了之后，server端的任务就完成了。

很简单，
路由匹配获取ssr.js -> await ssr.js 获取data -> data + funciton 获取view -> html模板 + view + data 返回给前端

## 前端获取，data
用户拿到了html文件，加载出来了。然后开始加载body尾部的打包文件。
我们进入到了前端的入口文件
打包文件加载完毕，最开始执行的就是脱水。
我们的数据通过html主导了window.SSRDATA之中。这里面取出来。


## 渲染（6. 前端，用相同的data，通过相同的function，得到相同的view1）
然后，我们和后端一样，调用了位于share的app根节点。并且把从后端拿到的store data原封不动的扔进去。
那么相同的data + 相同的app funciton 必然得到 = 相同的view。这就是同构的精华。

## end 哪些是同构的？ 那些不是同构的。
到目前为止，都是同构的
function是同构的。view视图是同构的。

下一秒后的副作用，就不同勾了。也不需要同构。ssr只是一个静态的，一瞬间的事情。
副作用不同构。
例如发起请求
设置window啥的。


其他细节
为什么前端 后端都需要注入数据？
不仅都要注入，而且数据必须相同。这样才能保证渲染出来一样的结果。


我的疑问。
1. react是怎么在现成的html里面，辨识出来组件的，而不是重新渲染他们。
2. 为什么如果前后端的dom结构又不一样，最终的结果会错乱。



## 部署
部署就很简单了
1. nginx监听80端口 将所有/ 请求转发到 3000ssr 将/api转发到业务上
2. ssr会获取build的html模板。需要配置一下static。
3. 