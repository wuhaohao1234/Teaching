# VueRouter

## 一、路由基础介绍
### 1.1 什么是前端路由
* 路由是根据不同的url地址展示不同的内容或页面
* 前端路由就是把不同的路由对应不同的内容或页面的任务交给前端来做，之前是通过服务端根据url的不同返回不同的页面实现的
### 1.2 什么时候使用前端路由
* 在单页面应用，大部分结构不变，只改变内容的使用

## 二、Router使用

* 进入src/views文件夹新建Other.vue

```
# src/views/Other.vue

<template>
  <div class="Other">
    <h1>这是Other路由</h1>
  </div>
</template>
```

* 进入src/router.js添加Other路由

    * 引入
    `import Other from './views/Other.vue'`
    * routes添加
    ```
    {
        path: '/other',
        name: 'other',
        component: Other
    }
    ```

* 完整代码

```
import Vue from 'vue'
import Router from 'vue-router'
import Home from './views/Home.vue'
import Other from './views/Other.vue'
Vue.use(Router)

export default new Router({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (about.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')
    },
    {
      path: '/other',
      name: 'other',
      component: Other
    },
  ]
})

```

## 三、App.vue中显示路由

```
<template>
  <div id="app">
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/other">other</router-link>
    <router-view/>
  </div>
</template>
<style lang="stylus">
a
  display :inline-block;
  margin : 1rem;
  color : #f80;
</style>
```

## 四、嵌套路由


```
import Vue from 'vue'
import Router from 'vue-router'
import Home from './views/Home.vue'
import Other from './views/Other.vue'
Vue.use(Router)

export default new Router({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (about.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')
    },
    {
      path: '/other',
      name: 'other',
      component: Other,
      children:[
          {
              path:'',
              name:'',
              component:''
          }
      ]
    },
  ]
})

```

## 五、js控制路由跳转

`this.$router.push("about")`