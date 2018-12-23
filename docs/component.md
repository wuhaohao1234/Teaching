# Vue组件
    经过前几章的学习，已经了解如何使用vue写页面,下面介绍vue一个新的概念组件
## 一、组件编写
1. 创建组件Mybox

    新建Mybox.vue文件

```
# src/components/Mybox.vue
<template>
    <div>
        <h2>我是Mybox组件</h2>
    </div>
</template>

<script>
export default {
    name:'Mybox'
}
</script>

<style lang="stylus" scoped>

</style>
```
2. 引入组件

```
# src/components/HelloWorld.vue
<template>
  <div>
    {{msg}}
    <hr>
    <Mybox/>
  </div>
</template>
<script>
import Mybox from './Mybox'

export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  components:{
    Mybox
  }
};
</script>
<style lang="stylus" scoped>
</style>

```

* 通过import Mybox from './Mybox'引入Mybox组件，可以不加.vue

* 通过components将组件引入

```
components:{
    Mybox
}
```

* 将组件挂载到页面上

```
<template>
  <div>
    {{msg}}
    <hr>
    <Mybox/>
  </div>
</template>
```

## 二、组件传入参数

* HelloWorld组件传入参数

    :name=msg

```
<template>
  <div>
    {{msg}}
    <hr>
    <Mybox :name=msg />
  </div>
</template>
<script>
import Mybox from './Mybox'

export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  components:{
    Mybox
  }
};
</script>
<style lang="stylus" scoped>
</style>

```

* Mybox组件接收参数name

```
<template>
    <div>
        <h2>我是Mybox组件</h2>
        <hr>
        {{name}}
    </div>
</template>

<script>
export default {
    props:['name'],
    name:'Mybox'
}
</script>

<style lang="stylus" scoped>

</style>
```

## 三、组件中函数的传递

* 父级组件HelloWorld

    传递@childClick=addClick @childInp=addInp

```
<template>
  <div>
    {{msg}}
    <hr>
    <Mybox :name=msg @childClick=addClick @childInp=addInp />
  </div>
</template>
<script>
import Mybox from './Mybox'

export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "原数据"
    };
  },
  methods:{
    addClick(){
      console.log('父级组件addClick')
    },
    addInp(){
      console.log('父级组件addInp')
    }
  },
  components:{
    Mybox
  }
};
</script>
<style lang="stylus" scoped>
</style>

```

* 子级组件Mybox

    通过this.$emit('函数名')使用父级组件传递函数

```
<template>
    <div>
        <h2>我是Mybox组件</h2>
        <hr>
        {{name}}
        <hr>
        <button @click="addClick" >接受父组件参数</button>
    </div>
</template>

<script>
export default {
    props:['name'],
    name:'Mybox',
    methods:{
        addClick(){
            this.$emit('childClick')
            this.$emit('childInp')
        }
    }
}
</script>

<style lang="stylus" scoped>

</style>
```

**通过函数之间的参数来完成父子组件通信**

## 四、父级组件调用自级组件的方法

* 给子级组件绑定ref

* 通过this.$refs.child.子组件方法调用

```
<Mybox ref="child" :name=msg @childClick=addClick @childInp=addInp />

console.log(this.$refs.child.dbClick)
```

## vue计算属性与监听器

[vue计算属性与监听器](https://wuhaohao1234.github.io/Teaching/#/watch)
