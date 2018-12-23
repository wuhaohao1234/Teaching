# vue中的数据绑定与指令

## 一、数据绑定

### 1.1通过{{msg}}绑定数据

* 在src/components/HelloWorld.vue中增加msg数据，并渲染到页面

```
# src/components/HelloWorld.vue

<template>
<div>
    <h1>HelloWorld Vue</h1>
    {{msg}}
</div>
</template>
<script>
export default {
    name:'HelloWorld',
    data(){
        return {
            msg:'我是绑定的数据'
        }
    }
}
</script>
```

* 这里通过data函数的返回值增加msg数据,并且在组件中只能这样增加数据,如果是在页面中可这样

```
# html
<div id="app">{{msg}}</div>
# javascript
var app = new Vue({
    el:'#app',//绑定页面上的dom
    data:{
        msg:'我是绑定的数据'
    }
})
```
### 1.2通过v-html指令绑定数据

```
<template>
  <div>
    <h1>HelloWorld Vue</h1>
    <span v-html="msg" ></span>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'我是绑定的数据'
    }
  }
}
</script>
```
### 1.3通过v-text绑定数据
```
<template>
  <div>
    <h1>HelloWorld Vue</h1>
    <span v-text="msg" ></span>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'我是绑定的数据'
    }
  }
}
</script>
```

**注意:**

* 如果数据是一段html代码
    * v-html可以将数据解析为html代码渲染到页面上
    * v-text只是纯文本解析
```
<template>
  <div>
    <h1>HelloWorld Vue</h1>
    <span v-html="msg" ></span>
    <span v-text="msg" ></span>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'<i>我是被解析的数据</i>'
    }
  }
}
</script>
```
* 使用{{msg}}在页面加载的时候会可能出现{{msg}}字段,使用指令可避免

## 二、属性绑定

### 2.1 v-bind指令

* v-bind:属性名="属性值"

```
<template>
  <div>
    <h1>HelloWorld Vue</h1>
    <span v-html="msg" ></span>
    <hr>
    <a target="block" v-bind:href="url" >到我的github</a>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'<i>我是被解析的数据</i>',
      url:'https://github.com/wuhaohao1234'
    }
  }
}
</script>
```

* 简写:属性名="属性值"

`<a target="block" :href="url" >到我的github</a>`

## 三、类名绑定

* 增加私有样式:style scoped

* 增加isActive布尔值

```
<template>
  <div>
    <h1>HelloWorld Vue</h1>
    <span class="red" v-html="msg" ></span>
    <hr>
    <a target="block" :href="url" >到我的github</a>
    <div v-bind:class="['active','red']" > 
      我的样式
    </div>
    <div v-bind:class="isActive?'active':'none'" > 
      我的样式
    </div>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'<i>我是被解析的数据</i>',
      url:'https://github.com/wuhaohao1234',
      isActive:true
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```

## 四、条件绑定

### 1.v-if

```
<template>
  <div>
    <span v-if="isActive" >
      看见
    </span>
    <span v-if="!isActive" >
      看不见
    </span>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      isActive:true
    }
  }
}
</script>
```
* 条件为不成立时,dom树中没有此元素

### 2.v-show

```
<template>
  <div>
    <span v-show="isActive" >
      看见
    </span>
    <span v-show="!isActive" >
      看不见
    </span>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'<i>我是被解析的数据</i>',
      url:'https://github.com/wuhaohao1234',
      isActive:true
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```

* 条件为不成立时,dom树中有此元素,只是隐藏

### 3.v-for循环遍历数组

* 不要下标

```
<template>
  <div>
    <ul>
      <li v-for="item in items" >
        {{item}}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      items:[
        '我是第一个数据',
        '我是第二个数据',
        '我是第三个数据'
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>
```

* 要下标

```
<template>
  <div>
    <ul>
      <li v-for="(item,key) in items" >
        {{key}}=>{{item}}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      items:[
        '我是第一个数据',
        '我是第二个数据',
        '我是第三个数据'
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```

* 遍历对象

```
<template>
  <div>
    <ul>
      <li v-for="(item,key,index) in items" >
        {{item}}=>{{key}}==>{{index}}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      items:{
        item0:'第0条数据',
        item1:'第1条数据',
        item2:'第2条数据',
        item3:'第3条数据',
        item4:'第4条数据',
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```
## 五、事件绑定

### 1.鼠标事件v-on:click

* 新建methods用来写入事件函数

* 通过v-on:click="addClick"绑定事件

```
<template>
  <div>
    <button v-on:click="addClick" >按钮</button>
    <p>{{msg}}</p>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'原数据'
    }
  },
  methods:{
    addClick(){
      console.log(1)
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```
* 简写:v-on:click转换为@clcik

* addClick中的event为事件对象

* 通过ref绑定dom,通过this.refs操作dom

```
<template>
  <div>
    <button @click="addClick" >按钮</button>
    <p ref="domP" >{{msg}}</p>
  </div>
</template>
<script>
export default {
  name:'HelloWorld',
  data(){
    return {
      msg:'原数据'
    }
  },
  methods:{
    addClick(event){
      console.log(this.$refs.domP)
      console.log(event)
    }
  }
}
</script>

<style lang="stylus" scoped>
.red
  color : red;
.active
  display : block;
.none
  display : none;
</style>

```

* 通过@click.stop="addClick"阻止冒泡

* 通过@click.prevent="addClick"阻止事件默认行为

```
<template>
  <div>
    <div @click="dbClick" >
      <button @click.stop="addClick" >按钮</button>
      <p ref="domP" >{{msg}}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  methods: {
    addClick(event) {
      console.log(this.$refs.domP);
      console.log(event);
    },
    dbClick(){
      console.log('冒泡')
    }
  }
};
</script>

<style lang="stylus" scoped>
.red {
  color: red;
}

.active {
  display: block;
}

.none {
  display: none;
}
</style>
```

### 2.键盘事件v-on:input

```
<template>
  <div>
    <div @click="dbClick" >
      <button @click.stop="addClick" >按钮</button>
      <p ref="domP" >{{msg}}</p>
      <input v-on:keyup.enter.stop="addUp" type="text">
    </div>
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  methods: {
    addClick(event) {
      console.log(this.$refs.domP);
      console.log(event);
    },
    dbClick(){
      console.log('冒泡')
    },
    addUp(event){
      console.log(event.keyCode)
    }
  }
};
</script>

<style lang="stylus" scoped>
.red {
  color: red;
}

.active {
  display: block;
}

.none {
  display: none;
}
</style>

```
## 六、双向数据绑定v-model

```
<template>
  <div>
    <input type="text" v-model="msg" >
    <hr>
    {{msg}}
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  methods: {
    
  }
};
</script>

<style lang="stylus" scoped>
.red {
  color: red;
}

.active {
  display: block;
}

.none {
  display: none;
}
</style>

``` 
## vue生命周期

[vue生命周期](http://localhost:3000/#/lifeCycle)
    