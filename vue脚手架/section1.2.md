# 参数配置

### 1、路径**：**

**      **   在table.vue组件中导入loading.vue组件

```
     import Loading from '../../../components/loading/loading.vue'
```

使用这种方式导入文件不方便，并且容易出错。项目结构如下，其中**build文件夹为项目构建\(webpack\)相关代码**

![](/assets/import.png)

### 解决方法： 别名配置

```
     查看 build / webpack.base.config.js文件。
```

```js
function resolve (dir) {
  return path.join(__dirname, '..', dir)
}

module.exports = {
    .......
    resolve: {
        .....
        alias: {
          '@': resolve('src'),
          'common': resolve('src/common'),
          'components': resolve('src/components'),
          'api': resolve('src/api'),
        }
  },  
}
```

在table.vue组件中，可以改修为：

```js
import Loading from 'components/loading/loading.vue'
```

**在vue文件使中**，用别名路径加载静态资源时\(样式文件，图片等\)，需要在路径前加上波浪号\(~\)，以下是home.vue组件的部分代码。

```js
<template>
......
    <img src='~common/images/logo.png'>
.....
</template>

.....

<style lang="stylus" rel="stylesheet/stylus"> 
@import 'scss_vars'

....
</style>
```

### 

### 2、本地图片无法显示

#### 通过v-bind指令动态绑定本地图片资源无法显示问题。

场景：通过变量保存图片的src路径，或者在v-for中循环显示图片。

```js
imgUrl : './test.png'

<img :src='imgUrl' />  // 此时webpack只会把它当做字符串处理从而找不到图片地址(即不会对该图片进行打包)，无法正确引用该本地图片

解决方法
1、将静态资源图片放在src同级别的static文件夹中。  webpack将static文件夹中的内容拷贝到项目运行的根目录下。不会编译与压缩

2、imgUrl: "require('./test.png')" ，该方法会将图片转成base64存在内存中

3、import avatar from './logo.png'
   imgUrl : avatar
```

### 

### 3、前后端分离，前端请求后台api接口

在开发环境









