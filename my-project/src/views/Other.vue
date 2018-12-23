<template>
  <div class="Other">
    <h1>这是Other路由</h1>
    <button @click='addHash' >点击</button>
  </div>
</template>

<script>
export default {
  name:'Other',
  methods:{
    addHash(){
      this.$router.push("about")
    }
  }
}
</script>
