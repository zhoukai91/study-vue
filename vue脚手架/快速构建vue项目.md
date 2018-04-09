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

CommonJS的核心思想：

> 把一个文件当做一个模块，通过require方法同步加载模块。

其同步加载模块的方案主要应用于\`node\`服务端

> Node.js的服务端编程加载的模块主要存在于服务器磁盘，所以加载速度较快，对node这种单线程，影响较小。

> 但是,



