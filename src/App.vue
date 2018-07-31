<template>
  <div id="app">
    <Header msg="Movies"/>
    <Gallery/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Gallery from './components/Gallery.vue'

export default {
  name: 'app',
  props: {
    msg: String
  },
  components: {
    Header,
    Gallery
  }
}
</script>

<style lang="less">
@import '~normalize.css';
// @import './assets/styles/variables.less';

#app {
  background-color:#1e2426;
  font-family:Verdana,Geneva,Tahoma,sans-serif;
  color:#fff;
  margin:0 auto;
  height:100vh;
  display:flex;
  flex-direction:column
}
</style>
