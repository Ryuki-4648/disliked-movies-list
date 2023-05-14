<template>
  <div>
    <HelloWorld msg="ぜったいに見たくない映画リストとは"/>
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
  color: #242021;
}
body {
  margin: 0;
  padding: 0;
}
</style>
