# Vue教程
这里默认你已经按照本文教程搭建环境,如果没有搭建，请回到主页搭建环境
[搭建环境](https://wuhaohao1234.github.io/Teaching/#/?id=%e8%ae%a4%e8%af%86vue%e5%b9%b6%e6%90%ad%e5%bb%ba%e7%8e%af%e5%a2%83)

## 认识目录

```
├── node_modules     # 项目依赖包目录
├── public
│   ├── favicon.ico  # ico图标
│   └── index.html   # 首页模板
├── src 
│   ├── assets       # 样式图片目录
│   ├── components   # 组件目录
│   ├── views        # 页面目录
│   ├── App.vue      # 父组件
│   ├── main.js      # 入口文件
│   ├── router.js    # 路由配置文件
│   └── store.js     # vuex状态管理文件
├── .gitignore       # git忽略文件
├── .postcssrc.js    # postcss配置文件
├── babel.config.js  # babel配置文件
├── package.json     # 包管理文件
```
    以上环节作为新手认识也没多大意思,本文教程将从src/components/HelloWorld.vue文件入手

## 还原教学环境

* 首先删除HelloWorld.vue内部所有代码,增加以下代码

```
//src/components/HelloWorld.vue
<template>
<div>
    <h1>HelloWorld Vue</h1>
</div>
</template>
<script>
export default {
name:'HelloWorld'
}
</script>
```
* 然后删除src/App.vue中的router与style
```
//src/App.vue
<template>
  <div id="app">
    <router-view/>
  </div>
</template>
```
* 最后删除src/views/Home.vue中的img

```
//src/view/Home.vue
<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  }
}
</script>
```
* 观察页面localhost:8080变化(删除只是为了方便教学,避免干扰)

## 正式开始Vue教学

[vue中的数据绑定与指令](https://wuhaohao1234.github.io/Teaching/#/start)
