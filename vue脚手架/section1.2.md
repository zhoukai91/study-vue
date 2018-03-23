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

### 3、本地图片无法显示

通过v-bind指令动态绑定本地图片资源无法显示问题。

