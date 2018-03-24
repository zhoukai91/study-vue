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





