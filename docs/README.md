# 认识Vue并搭建环境

## 一、初识

* Vue框架是一个MVVM框架，Module和view是双向绑定的。vue没有控制器的概念，它的核心思想是数据驱动，状态管理，以及组件化。
* 因此在我们js编程中，不会去操作DOM、class，更多的关注我们的数据层面。去改变一个变量，通过变量来控制我们的视图，通过事件绑定、状态管理来进一步渲染视图。
* MVVM框架的特点是没有控制器，通过view和module来进行交互，实际上底层已经帮我们封装了

### 1.1概况

* Vue本身不是一个框架
* Vue结合周边的生态构成一个灵活的、渐进式的框架

### 1.2核心思想

* 数据驱动【只关注数据层面】
* 组件化

### 1.3双向数据绑定

**Object.defineProperty在双向绑定中起来很重要作用**

```
<input type="text" id="userName">
<span id="uName">
```
```
var obj = {}

object.defineProerty(obj,"userName",{
    get:()=>{
        
    },
    set:(val)=>{
        $("#uName").innerHTML = val
        $("#userName").value = val;
    }
})
$("#userName").on("keyup",function(){
    obj.userName = event.target.value
})
```
## 二、环境搭建

### 2.1依赖工具

    在构建一个 Vue 项目前，我们先要确保你本地安装了 Node 环境以及包管理工具 npm，打开终端运行：
```
    # 查看 node 版本
    node -v

    # 查看 npm 版本
    npm -v
```

### 2.2安装 Vue CLI 3.x

`npm i -g @vue/cli`

### 2.3初始化项目

`vue create my-project`

    执行完上述命令后，会出现一系列的选择项，我们可以根据自己的需要进行选择，流程图如下

1. 这里选择默认配置(Manually)

2. 选择Babel、Router、Vuex、CSS Pre-processors

3. cssLoader选择stylus

4. 选择eslint代码检查工具

5. package.json配置文件

6. 打开项目目录

`cd my-project`

7. 启动项目,并在8080端口监听

`npm run serve`

8. 可能出现的问题

    控制台报错 Invalid Host/Origin header

    * 解决办法:
    根目录新建vue.config.js
    ```
    module.exports = {
        // webpack-dev-server 的配置项
        devServer: {
            host: '0.0.0.0',
            disableHostCheck: true
        }
    }
    ```
    * 原因:热加载无效
    
    与之前的项目对比 package-lock.json 文件，发现 webpack-dev-server 的版本从 3.1.10 -> 3.1.11 
    
## 进入下一章教学
[vue项目目录介绍与还原教学环境](http://localhost:3000/#/Vue)