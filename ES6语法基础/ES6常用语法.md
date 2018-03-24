### 变量声明

```js
var a , b;   // 确定：变量提前
```

##### ES6写法：

```js
// 不可以在定义前使用，块级作用域 

console.log(a)   
if (true) {
    let a = 1 , b = 0; 
}

// 定义常量
const PI = 3.14
```

### 

### 模板字符串

```js
var str = 'world';
var result = 'hello' + str;
```

##### ES5写法：

```js
// 使用反引号 
var str = 'world';
var result = `hello ${str}`;
```



### 模块 \(ES5原生不支持\)

##### ES6中：

\(1\)按需导入

```js
// 文件 config.js， 导出模块
const A = {
    name: 'zk'
};
const B = {
    name: 'wl'
};

export const A
export const B

```

```js
// main.js 用到，导入模块
import {A} from './config.js'
import {B} from './config.js'
import {A，B} from './config.js'



// 
```



