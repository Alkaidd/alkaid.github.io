<template>
  <div class="home">
    <div class="g-bg">
      <MySideTab ref="mySideTab"></MySideTab>
      <MyFooterTab></MyFooterTab>
    </div>
    <LightRain/>
  </div>
</template>

<script>
// @ is an alias to /src
import LightRain from '../components/LigthRain/index.vue'
import MySideTab from '@/components/MySideTab/index.vue'
import MyFooterTab from '@/components/MyFooterTab/index.vue';

export default {
  name: 'HomeView',
  components: {
    LightRain,
    MySideTab,
    MyFooterTab
  },
  methods: {
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
