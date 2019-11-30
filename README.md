 # Best Practice
 
 * 通过让路由的父级渲染一个单独的 router-view 组件，来实现多级路由的嵌套关系
 
 ```javascript
 {
    path: '/survey',
    name: 'questionnaire',
    component: {
        render: h => (
            <keep-alive>
                <router-view />
            </keep-alive>
        )
    },
    children:[
     //...
    ]
}
 ```
 
 * 路由name按照层级命名  [Vue路由自动注入实践](https://juejin.im/post/5cb4ad82e51d456e7e297bbf)
 
 ```javascript
 {
    component: () => import('@/views/Withdraw/Result/Description/Index.vue'),
    name: 'withdraw-result-description',
    path: '/withdraw/result/description'
}
 ```

 * 避免使用魔术数字，声明常量保存魔术数字
 
 ```javascript
 const SELECTED = 1
 
 if(x === SELECTED){
 //...
 }
 ```
 
 * DOM/自定义事件处理程序的函数名用 handle 作为开头
 
 ```javascript
 // html
  <button onclick="handleClick"></button>
  // Vue template
  <hello-world @close="handleClose"></hello-world>
 ```
 
 * 没有权限页面跳转后使用 replace 替换页面,而不是push
 
 * `markdown高亮`
 
 * markdown 子目录 
   *  子目录
 
 * select框保存 option 选项的数组用 options 作为开头
 
 ```vue
   <el-option
      v-for="item in optionsClass"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option
 ```
 
 * 在声明 prop 时使用驼峰或者帕斯卡命名，template模版中使用短横线
 ```vue
 // camel-case
 <my-component my-prop>
 
 // Pascal
 <MyComponent my-prop />
 ```
 
 * Vue自定义事件，使用短横线命名
 
 ```javascript
 this.$emit('my-event')
 ```

 * [浏览器下载文件插件FileSaver](https://github.com/eligrey/FileSaver.js)
 
 * 封装条件语句
 
 ```javascript
 const isComplexDataType = obj => (typeof obj === 'object' || typeof obj === 'function') && (obj !== null)
 
 if(isComplexDataType(something)){
  //.......
 }
 ```

* [Vue风格指南](https://cn.vuejs.org/v2/style-guide/)
 
* 使用逻辑运算符（&& ||）替换三元运算符（适合不需要第二个条件的情况）

```javascript
hasMoney ? console.log('有钱') : null

hasMoney && console.log('有钱')
```
 
* 尽量不要用取反(!)作为判断条件 
 
* 使用函数默认值替代备用的选项

* 验证使用 handleValidate,搜索使用 handleSearch,提交用 handleSubmit

* 日期格式化轻量级库[day.js](https://github.com/iamkun/dayjs)

* 减少嵌套，尽早return

```javascript
function test(fruit, quantity) {
  const redFruits = ['apple', 'strawberry', 'cherry', 'cranberries'];
  if (!fruit) throw new Error('No fruit!'); // condition 1: throw error early
  if (!redFruits.includes(fruit)) return; // condition 2: stop when fruit is not red
  console.log('red');
  // condition 3: must be big quantity
  if (quantity > 10) {
    console.log('big quantity');
  }
}
```

* 封装函数时，尽量使用函数表达式取代语句，表达式有返回值，语句没有返回值（尽量使用纯函数，防止影响其他代码）

```javascript
function setBackgroundColor(ele, color) {
    ele.style.backgroundColor = color;
    return color;
}

// 多处使用
var ele = document.querySelector('.test');
setBackgroundColor(ele, 'red');
setBackgroundColor(ele, '#ccc');
```

* [编辑和创建的界面差不多可以使用同一组件,在路由的meta信息中标注是那个功能](https://juejin.im/post/593121aa0ce4630057f70d35)

![](https://lc-gold-cdn.xitu.io/25969342df96a2000ec6?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

```javascript
computed: {
  isEdit() {
    return this.$route.meta.isEdit // 根据meta判断
    // return this.$route.path.indexOf('edit') !== -1 // 根据路由判断
  }
}，
created() {
  if (this.isEdit) { 
    this.fetchData();
  }
}
```

* 修改 elementui 框架样式时,使用 `::v-deep` 作为深度选择器

```css
::v-deep .el-tree {
//....
}
```


# TodoList

* [ ] 写个前端文件上传的解决方案（博客）

* [ ] 学习 macOS 命令行

* [ ] ~~将红宝书的纸质笔记记录到博客上~~水文不想写了

* [ ] 买本书学习Linux（鸟叔的私房菜）

* [x] 写篇解析vue-router源码的博客

* [x] 写个element的表单验证组件

* [x] 写个给图片资源添加preload的webpack plugin

* [ ] 自己实现一个简易的vue（包括vue-router,vuex）

* [x] [冴羽博客](https://github.com/mqyqingfeng/Blog)

* [x] 看Vue源码

* [x] 学习数据结构与算法

* [ ] 刷leetCode(ing~)

* [x] 看完这个[前端进阶](https://www.jianshu.com/p/996671d4dcc4)

* [x] ~~使用vue+typescript重构公司项目~~重构公司项目



