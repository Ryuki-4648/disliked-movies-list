<template>
  <div>
    <img alt="ぜったいに見たくない映画リスト" src="./assets/logo.png" class="logo">
    <HelloWorld msg="ぜったいに見たくない映画リスト"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: YuGothic,'Yu Gothic','ヒラギノ角ゴシック','Hiragino Sans',sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.logo {
  display: block;
  margin: 80px auto 140px;
}
</style>
