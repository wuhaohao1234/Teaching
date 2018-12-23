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