<template>
  <div id="app">
    <layout>
      <img alt="Vue logo" src="./assets/logo.png">
      <HelloWorld msg="Welcome to Your Vue.js App"/>
    </layout>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Layout from './layout'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Layout
  }
}
</script>

<style lang="scss">
  html,body {
    height: 100%;
  }
  #app, #app > .layout {
    min-height: 100%;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
  .page-content {
    text-align: center;
  }
}
.is-full-height {
  min-height: calc(100% + .75rem);
}
</style>
