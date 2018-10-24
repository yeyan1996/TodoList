# TodoList & Standard
1. 在data() {}中加入处理函数在return数据，可以考虑用proxy拦截验证数据？（vue-element-admin）
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

2. 管理系统的input组件和table组件2者不要分离

3. 统一把icon-class换成svg的形式

4. async/await使用.catch()捕获错误

```
async function F() {
    let res = await fetch('http://localhost:3000',{
        method:'GET'
    }).catch(err=>console.log(err))
    let data = await res.json().catch(err=>console.log(err))
}
F()
```