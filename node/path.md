path模块，是用来确认路径的。

context是用来手动指定根路径

__dirname
false: 闭嘴。听node的。
true: 相对于context
mock: /

node在webpack打包后的确变成了/ 需要重置一下
另外，cra似乎建议，将current work dir 作为一个基本的。


path.resolve似乎会很努力，把传入的相对路径，转化为绝对的。
当实在没有绝对路径告诉他的时候。他只能按照执行脚本的node所在路径来作为。并且返回了。（就记住，他是绝对路径的忠实热爱者）
---

webpack config
html


---

css-loader的用处是：
将css文件，解析成一个数组。
如果再配合一个xxx
他就能将这个数组。打到style 上。

就这么简单。


那么实际上，服务端，并不需要这个过程。因为反正也没有style在上面。
我们关注的是css文件。那个是通过链接上来的。


服务端只关心，server.js这个文件。

---
