<template>
  <div>
    {{msg}}
    <hr>
    <button @click="slChild" >调用子组件的方法</button>
    <Mybox ref="child" :name=msg @childClick=addClick @childInp=addInp />
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
    },
    slChild(){
      console.log(this.$refs.child.dbClick)
      this.$refs.child.dbClick()
    }
  },
  components:{
    Mybox
  }
};
</script>
<style lang="stylus" scoped>
</style>
