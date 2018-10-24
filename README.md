 # Standard
 
* 管理系统的input组件和table组件2者不要分离,每次搜索先清除表格数据,再执行搜索操作

* 统一把icon-class换成svg的形式

* async/await使用.catch()捕获错误(**或者使用拦截器对状态码不等于200的统一拦截?**)

```
async function F() {
    let res = await fetch('http://localhost:3000',{
        method:'GET'
    }).catch(err=>console.log(err))
    let data = await res.json().catch(err=>console.log(err))
}
F()
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

# TodoList
* 在data() {}中加入处理函数在return数据，可以考虑用proxy拦截验证数据？（vue-element-admin）
```
data() {
    const validateUsername = (rule, value, callback) => {
      if (!isvalidUsername(value)) {
        callback(new Error('Please enter the correct user name'))
      } else {
        callback()
      }
    }
    const validatePassword = (rule, value, callback) => {
      if (value.length < 6) {
        callback(new Error('The password can not be less than 6 digits'))
      } else {
        callback()
      }
    }
    return {
      loginForm: {
        username: 'admin',
        password: '1111111'
      },
      loginRules: {
        username: [{ required: true, trigger: 'blur', validator: validateUsername }],
        password: [{ required: true, trigger: 'blur', validator: validatePassword }]
      },
      passwordType: 'password',
      loading: false,
      showDialog: false,
      redirect: undefined
    }
  },
```

* 用户点击左侧导航栏的时候,如果跳转的页面和当前页面一致,就return

* 登出按钮的函数只要给vuex发送一个logout的dispatch,在vuex中的actions中把登录信息(sessionStorage或token)删除,在then()中刷新页面,然后通过vue-router的权限验证自动弹回主页
