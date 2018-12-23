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
