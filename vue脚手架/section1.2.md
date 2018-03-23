# 参数配置

### 1、**场景一：**

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
          'components': resolve('src/components'),
        }
  },  
}
```

在table.vue组件中，可以改修为：

```js
import Loading from 'components/loading/loading.vue'
```



