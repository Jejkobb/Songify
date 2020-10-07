<template>
  <div id="app">
    <Header msg="Låtify"/>
    <youtube style="display:none" :video-id="videoID" :playerVars="{autoplay: 1}" @ready="ready"></youtube>
    <List/>
    <Paster :genre="this.genre" :songs="this.songs"/>
    
    <!--<Player :genre="this.genre"/>-->
    <div class="footer">
      <h2 v-if="!playing">
        Now playing: {{songTitle}}
      </h2>
      <img id="prev" @click="prev" src="./assets/prev.png">
      <img v-if="playing" @click="toggleUrl" id="play" src="./assets/play.png">
      <img v-else @click="toggleUrl" id="pause" src="./assets/pause.png">
      <img id="next" @click="next" src="./assets/next.png">
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Paster from './components/Paster.vue'
import List from './components/List.vue'
var getYoutubeTitle = require('get-youtube-title')

export default {
  name: 'App',
  components: {
    Header,
    Paster,
    List,
  },
  data() {
    return {
      videoID: "",
      genre: 0,
      currentSong:0,
      songs: "",
      songTitle: "",
      playing: true,
      Songs: [
        [], //your que
        ["UNZqm3dxd2w","xpVfcZ0ZcFM","DRS_PpOrUZ4","U9BwWKXjVaI"], //popular
        ["SLsTskih7_I","UceaB4D0jpo","ba7mB8oueCY","ApXoWvfEYVU"], //rock
        ["w2Ov5jzm3j8","r_0JjYUe5jo","8CdcCD5V-d8","NQbkGDoD7B0"]  // rap
      ]
    }
  },
  methods: {
    ready (event) {
      this.player = event.target;
    },
    toggleUrl(){
      this.playing = !this.playing;
      if(this.playing == false){
        this.player.playVideo();
      }else{
        this.player.pauseVideo();
      }
    },
    changeTitle(title){
      this.songTitle = title;
    },
    prev(){
      if(this.Songs[this.genre].length <= 1){
        return;
      }
      this.currentSong = this.currentSong-1 < 0 ? this.Songs[this.genre].length-1 : this.currentSong-1;
      this.playSong(this.currentSong);
    },
    next(){
      if(this.Songs[this.genre].length <= 1){
        return;
      }
      this.currentSong = this.Songs[this.genre].length > this.currentSong+1 ? this.currentSong+1 : 0;
      this.playSong(this.currentSong);
    },
    playSong(id){
      this.videoID = this.Songs[this.genre][id];
      this.currentSong = id;
      console.log(this.Songs);
      this.playing = false;
      this.player.playVideo();
      getYoutubeTitle(this.videoID, (e, t) => {
        this.songTitle = t;
      });
    }
  },
  mounted: function () { 
    this.$root.$on('changeGenreEvent', (genre) => { // here you need to use the arrow function
     this.genre = genre;
     this.currentSong = 0;
     this.playSong(this.currentSong);
     console.log("this.genre: " + this.genre);
    })

    this.$root.$on('changeSong', (videoID) => { // here you need to use the arrow function
     this.videoID = videoID;
     this.Songs[0].push(videoID);
     this.currentSong = 0;
     console.log(this.Songs);
     this.playing = false;
     this.player.playVideo();
     getYoutubeTitle(videoID, (e, t) => {
       this.changeTitle(t);
     });
     console.log("this.videoID--: " + videoID);
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
.footer {
   position: fixed;
   left: 0;
   bottom: 0;
   width: 100%;
   background-color: #555;
   color: white;
   text-align: center;
}
img {
  cursor: pointer;
  transition: all 0.2s ease;
}
img:hover {
  transform: scale(1.1);
}
img:active {
  transform: scale(0.9);
}
#play, #pause {
  height: 54px;
  margin: 12px;
}
#prev, #next {
  margin: 24px;
}
</style>
