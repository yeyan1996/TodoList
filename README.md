 # Best Practice
 
* 管理系统的input组件和table组件2者不要分离,每次搜索先清除表格数据,再执行搜索操作

* 统一把icon-class换成svg的形式

* 验证使用handleSubmit,搜索使用handleSearch

* 路由跳转的函数名使用linkXXX
```
   linkEdit() {
                this.$router.push({
                    name:'hospManagement'
                })
            }
```


* 所有api分离成单独的文件管理
```
/api/list.js
import axios from '../../axios' //引入配置好的axios
export function fetchList(query) {
  return axios(
  url:'/xxxxx',
  method:'get',
  params:query
  )
}

/list.vue
import {fetchList} from 'api/list.js'
......
await fetchList().catch(err=>console.log(err))

```

* scss写在vue文件里面,创建style文件,放入公共的全局样式,以及mixin封装的样式,以及variables变量单独存储统一颜色,以及elementui自定义的样式

* 日期格式化插件[date-format](https://www.npmjs.com/package/date-format)
```
npm i date-format -D
```

* 减少嵌套，尽早return
```
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

* 封装函数时，尽量使用函数表达式取代语句，表达式有返回值，语句没有返回值
```
function setBackgroundColor(ele, color) {
    ele.style.backgroundColor = color;
    return color;
}

// 多处使用
var ele = document.querySelector('.test');
setBackgroundColor(ele, 'red');
setBackgroundColor(ele, '#ccc');
```
* ~~currentTableData放在computed里面,值是currentPage和tableData计算后的结果~~

    封装了分页器组件,每次分页向父组件触发currentChange事件

* vuex的store文件创建一个mutations-types
```
 ballInCart({commit}, boolean) {
    commit(types.BALL_IN_CART, boolean);
  }
```

* 如果一个模块下就一个文件，尽量写成 index.vue 。这里文件夹和文件同名，路由是不是很长？你在其他文件中 import 的时候是不是也不方便？ 而且我发现 problemManagement 和 problemRetrieve 都属于问题管理模块，完全可以合并到一个文件夹里啊。还有，文件夹已经表明是问题管理模块了，所以文件名就不要再以 problem*** 开头了。
```
problemManagement
│   ├── index.vue
│   ├── retrieve.vue
qualityCheckAppeal
    └── index.vue
```

# TodoList
* [ ] 学习数据结构与算法

* [ ] 看完这个[前端进阶](https://www.jianshu.com/u/10ae59f49b13)

* [ ] ~~使用vue+typescript重构公司项目~~

      重构公司项目,提取多个公共组件

* [ ] 登出按钮的函数只要给vuex发送一个logout的dispatch,在vuex中的actions中把登录信息(sessionStorage或token)删除,在then()中刷新页面,然后通过vue-router的权限验证自动弹回主页

