<template>
  <div class="home">
    <div class="g-bg">
      <img alt="Vue logo" src="../assets/logo.png">
      <HelloWorld msg="Welcome to Your Vue.js App"/>
    </div>
    <LightRain/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import LightRain from '../components/LigthRain/index.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    LightRain
  }
}
</script>

<style lang="less">
.g-bg {
  position: fixed;
  width: 100vw;
  height: 100vh;
}
</style>
