<template>
  <div id="app">
    <Header msg="Låtify"/>
    <Paster/>
    <Player/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Paster from './components/Paster.vue'
import Player from './components/Player.vue'

export default {
  name: 'App',
  components: {
    Header,
    Paster,
    Player,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f1f1f1;
  margin-top: 60px;
}
body {
  padding: 0;
  margin: 0;
  background-color: #333;
}
</style>
