# Vue计算属性与监听器

## 一、watch监听器

    用来监听数据变化，并做出相应的行为

```
# Mybox.vue
<template>
    <div>
        <h2>我是Mybox组件</h2>
        <hr>
        {{name}}
        <hr>
        <button @click="addClick" >接受父组件参数</button>
        <hr>
        监听器
        <input type="number" v-model="age"><br>
        <p>{{infoMsg}}</p>
    </div>
</template>

<script>
export default {
  props: ["name"],
  name: "Mybox",
  data() {
    return {
      age: 10,
      infoMsg: ""
    };
  },
  watch: {
    age: {
      handler(val, oldVal) {
        var that = this;
        if (val > 0 && val < 15) {
          that.infoMsg = "你还是个小孩";
        } else if (val > 15 && val < 25) {
          that.infoMsg = "你已经是个少年";
        } else {
          that.infoMsg = "你已经长大了";
        }
      },
      deep:true
    }
  },
  methods: {
    addClick() {
      this.$emit("childClick");
      this.$emit("childInp");
    },
    dbClick() {
      console.log("被调用");
    }
  }
};
</script>

<style lang="stylus" scoped>
</style>
```

* watch为一个对象,监控age
* handler为行为函数,接受val新值与oldVal旧值,这里的val代表age
* deep为true代表深度监听，可以监听对象内部的多有数据

## 二、计算属性

    主要用途:当有缓存的时候，不会重复计算

* 通过computed写入reservename方法
* 视图层只需调用reservename

```
<template>
    <div>
        <h2>我是Mybox组件</h2>
        <hr>
        {{name}}
        <hr>
        <button @click="addClick" >接受父组件参数</button>
        <hr>
        监听器
        <input type="number" v-model="age"><br>
        <p>{{infoMsg}}</p>
        <p>
            {{reservename}}
        </p>
    </div>
</template>

<script>
export default {
  props: ["name"],
  name: "Mybox",
  data() {
    return {
      age: 10,
      infoMsg: ""
    };
  },
  watch: {
    age: {
      handler(val, oldVal) {
        var that = this;
        if (val > 0 && val < 15) {
          that.infoMsg = "你还是个小孩";
        } else if (val > 15 && val < 25) {
          that.infoMsg = "你已经是个少年";
        } else {
          that.infoMsg = "你已经长大了";
        }
      },
      deep:true
    }
  },
  methods: {
    addClick() {
      this.$emit("childClick");
      this.$emit("childInp");
    },
    dbClick() {
      console.log("被调用");
    }
  },
  computed:{
      reservename(){
          console.log(this.name)
          return this.name.split('').reverse().join('')　
      }
  }
};
</script>

<style lang="stylus" scoped>
</style>
```

## VueRouter
[VueRouter](https://wuhaohao1234.github.io/Teaching/#/router)