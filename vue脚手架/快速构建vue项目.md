# vue脚手架

> **        官方介绍**：Vue 提供一个命令行工具，可用于快速搭建大型单页应用。该工具为现代化的前端开发工作流提供了开箱即用的构建配置。只需几分钟即可创建并启动一个带热重载、保存时静态检查以及可用于生产环境的构建配置的项目

vue脚手架通过node进行构建，所以需要对node的知识有一定的了解。同时，vue-cli使用webpack进行前端工程化，因此，还需要对webpack简单了解！

```
# 全局安装 vue-cli
```

```
$ npm install --global vue-cli


# 创建一个基于 webpack 模板的新项目


$ vue init webpack my-project


# 安装依赖，走你


$ cd my-project


$ npm run dev   // 其他脚本命令可以在packge.json文件中查看
```

### 

### 

## 1、CommonJS规范

1、核心思想：

> 把一个文件当做一个模块，通过require方法同步加载模块。

2、应用场景

> Node.js的服务端编程加载的模块主要存在于服务器磁盘，所以加载速度较快，对node这种单线程，影响较小。因此，CommonJS同步加载模块方案主要应用于**node**服务端。

3、不适用于浏览器环境

> 浏览器加载方式与服务端完全不同。如果浏览器请求服务器资源时，会由于某个请求加载的时间过长导致浏览器阻塞，不会往下执行，所以就会出现网页打开缓慢的现象。并且，浏览器端是以插入&lt;script&gt;标签的形式来加载资源（ajax方式不行，有跨域问题），没办法让代码同步执行，使用commonJS同步写法会直接报错。

4、示例

```js
// 1.js
module.export = function() {
        say: function() {
            alert("你好");
        }
    }

// main.js
var a = require('./a.js');
a.say();
```

浏览器环境下必须采用异步模式。所以就有了 AMD，CMD 解决方案。

## 2、AMD规范

AMD\(异步模块定义\)是RequireJS在推广过程中对模块化定义的规范化产出。

1、核心思想：

> 异步加载所需的模块，然后在回调函数中执行主逻辑。

**可以并行加载多个模块，等所有模块都加载并且解释执行完成后**，才会执行接下来的代码，

2、吐槽点

> “提前执行”：所有依赖模块会被预先下载，并且提前执行（不管该模块的调用时机）。“提前执行”的性能消耗是不容忽视。

3、懒加载

> AMD保留了commonjs中的require、exprots、module这三个功能。因此，为了解决“提前执行”的性能消耗，依赖的模块不写在dependencies数组中，

4、示例

```js
// a.js
define(function(){
     return {
          say: function(){
               console.log('hello, a.js');
          }
     }
});

// b.js
define(function(){
     return {
          say: function(){
               console.log('hello, a.js');
          }
     }
});

// main.js
require(['a', 'b'], function(a, b){
     a.say();
     $('#b').click(function(){
          b.say();
     });
})

// AMD懒加载方式
// main.js
require(['a'], function(a){
     a.say();
     $('#b').click(function(){
           require(['b'], function(b){
               b.say();
          });
     });
})
```

这种懒加载减轻了初始化操作。**但是，在需要执行b.say\(\)时，需要实时下载代码然后在回调中才能执行，用户的操作会有明显的延迟卡顿。**

## 2、CMD规范

CMD\(同步模块定义\)是SeaJS\(淘宝团队\)在推广过程中对模块化定义的规范化产。

1、示例

```
// a.js
define(function(){
     return {
          say: function(){
               console.log('hello, a.js');
          }
     }
});


// main.js
define(function(require, exports, module){
     var a = require('a');
     a.say();
})


```



