每个node里面的js 都有一个神奇的module对象(我不知道他从哪里来的)

它里面有一些属性和方法

其中有一个是
exports = module.exports

因此exports.a = module.

当require的时候,其实就是把这个值拿到



http://nodejs.cn/api/modules.html
node文档

https://nodejs.org/en/knowledge/getting-started/what-is-require/
node解释require

http://javascript.ruanyifeng.com/nodejs/module.html
中文文档解释