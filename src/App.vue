<template>
  <div id="app">
    <Header msg="Låtify"/>
    <youtube style="display:none" :video-id="videoID" :playerVars="{autoplay: 1}" @ready="ready"></youtube>
    <List/>
    <Paster :genre="this.genre"/>
    
    <Player/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Paster from './components/Paster.vue'
import Player from './components/Player.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    Header,
    Paster,
    List,
    Player,
  },
  data() {
    return {
      videoID: "T9QXsopqOpA",
      genre: 0
    }
  },
  methods: {
    ready (event) {
      this.player = event.target;
    }
  },
  mounted: function () { 
    this.$root.$on('changeGenreEvent', (genre) => { // here you need to use the arrow function
     this.genre = genre;
     console.log("this.genre: " + this.genre);
    })
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
