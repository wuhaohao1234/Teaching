# Vue生命周期

```
<template>
  <div>
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
  beforeCreate() {
    console.group("------beforeCreate创建前状态------");
    console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
    console.log("%c%s", "color:red", "data   : " + this.$data); //undefined
    console.log("%c%s", "color:red", "message: " + this.message);
  },
  created() {
    console.group("------created创建完毕状态------");
    console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
    console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
    console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
  },
  beforeMount() {
    console.group("------beforeMount挂载前状态------");
    console.log("%c%s", "color:red", "el     : " + this.$el); //已被初始化
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
    console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
  },
  mounted() {
    console.group("------mounted 挂载结束状态------");
    console.log("%c%s", "color:red", "el     : " + this.$el); //已被初始化
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
    console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
  },
  beforeUpdate() {
    console.group("beforeUpdate 更新前状态===============》");
    console.log("%c%s", "color:red", "el     : " + this.$el);
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data);
    console.log("%c%s", "color:red", "message: " + this.message);
  },
  updated() {
    console.group("updated 更新完成状态===============》");
    console.log("%c%s", "color:red", "el     : " + this.$el);
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data);
    console.log("%c%s", "color:red", "message: " + this.message);
  },
  beforeDestroy() {
    console.group("beforeDestroy 销毁前状态===============》");
    console.log("%c%s", "color:red", "el     : " + this.$el);
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data);
    console.log("%c%s", "color:red", "message: " + this.message);
  },
  destroyed() {
    console.group("destroyed 销毁完成状态===============》");
    console.log("%c%s", "color:red", "el     : " + this.$el);
    console.log(this.$el);
    console.log("%c%s", "color:red", "data   : " + this.$data);
    console.log("%c%s", "color:red", "message: " + this.message);
  }
};
</script>
<style lang="stylus" scoped>
</style>
```
```
------beforeCreate创建前状态------
el     : undefined
data   : undefined
message: undefined
------created创建完毕状态------
el     : undefined
data   : [object Object]
message: undefined
------beforeMount挂载前状态------
el     : undefined
undefined
data   : [object Object]
message: undefined
------mounted 挂载结束状态------
el     : [object HTMLDivElement]
<div data-v-469af010 msg=​"Welcome to Your Vue.js App">​
  原数据
​</div>​
data   : [object Object]
message: undefined
```

## 应用举例

### 初始化input框获得焦点
```
<input ref="input" name="text" />

mounted() {
    this.$refs.input.focus()
},
```

### 定时器
```
<template>
  <div>
    {{msg}}
    <input ref="input" name="text" />
    <button @click="addClick" >点击</button>
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
  methods:{
    addClick(){
      clearInterval(this.timer)
    }
  },
  beforeCreate() {
  },
  created() {
  },
  beforeMount() {
    this.timer = setInterval(() => {
      console.log(1)
    }, 100);
  },
  mounted() {
    this.$refs.input.focus()
  },
  beforeUpdate() {
  },
  updated() {
  },
  beforeDestroy() {
    clearInterval(this.timer)
  },
  destroyed() {
  }
};
</script>
<style lang="stylus" scoped>
</style>

```

## Vue组件

[Vue组件](https://wuhaohao1234.github.io/Teaching/#/component)