<template>
  <div id="app">
    <Header msg="Låtify"/>
    <youtube style="display:none" :video-id="videoID" :playerVars="{autoplay: 1}" @ready="ready"></youtube>
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
  },
  data() {
    return {
      videoID: "T9QXsopqOpA"
    }
  },
  methods: {
    ready (event) {
      this.player = event.target;
    },
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
