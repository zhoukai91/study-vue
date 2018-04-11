### 转变思想

**vue   数据驱动**

### 组件化开发

将功能模块写成组件，提高开发效率

### 生命周期

vue组件的生命周期：

![](/assets/vue生命周期.jpg)

### 组件通信

```js
vue2.0组件间事件派发与接收  https://segmentfault.com/a/1190000008018314

        1、 父子组件通信，使用自定义事件, 子组件通过this.$emit出发事件， 在父组件的子组件元素中，通过@自定义事件名 接受事件
            子组件a @click='addCart' methods: {addCart(event){ this.$emit('add', event.target) } }
            父组件b <a @add='addFood'></a> methods: { addFood(){ ... } }


        2、通过new Vue对象，专门管理事件，可以非父子组件通信
              mian.js  eventHub : new Vue()
                    组件a     this.$root.$emit('eName',)
                    组件b     this.$root.$on('eName', () => {});


        3、 使用Vuex
```

#### 

#### vuex流程：



state \(状态\)

变化\(mutations\)

actions\(动作\)

![](/assets/vuex.png)

