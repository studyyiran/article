https://nodejs.org/api/http.html

我看看下 后端http 最基本的 createServer


这个之前写过一个demo。
先看下报错为什么会失效
然后使用聚沙成塔+番茄？

http.createServer(请求处理函数)

里面有req，res，他们是两个流。

req流
我可以获取他们的url method header

很有趣的是，如果是get的话，那就结束了
但如果是post，我可以通过
req.on data end 来进行流的监听。
然后一点点的写入stream
来达成


res流
我可以
setStatus
setHeader
我可以写入res.write res.end





复习锚点

req和res都是流。
通过流，我们可以往里面不断的写入数据，例如读取一个文件到另外一个文件。
这样会非常节约空间。



应用
1）渐进式开发。我可以通过将流慢慢写进来，然后降低服务器返回数据的间隔





