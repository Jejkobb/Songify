<template>
  <div class="footer">
    <img id="prev" @click="prevSong(currentSong,genre,Songs)" src="../assets/prev.png">
    <img v-if="!playing" @click="toggleUrl" id="play" src="../assets/play.png">
    <img v-else @click="toggleUrl" id="pause" src="../assets/pause.png">
    <img id="next" @click="nextSong(currentSong,genre,Songs)" src="../assets/next.png">
  </div>
</template>

<script>
export default {
  name: 'Player',
  props:{
    vidoeID: String,
    genre: Number
  },
  data() {
    return {
      playing: false,
      currentSong:0 ,
      currentGenre:0,
      Songs: [
        ["4NRXx6U8ABQ","GrAchTdepsU","YH9Nwa0RvO8","l0U7SxXHkPY"],
        ["UNZqm3dxd2w","xpVfcZ0ZcFM","DRS_PpOrUZ4","U9BwWKXjVaI"],
        ["SLsTskih7_I","UceaB4D0jpo","ba7mB8oueCY","ApXoWvfEYVU"],
        ["w2Ov5jzm3j8","r_0JjYUe5jo","8CdcCD5V-d8","NQbkGDoD7B0"]
      ]
    }
  },
  methods: {
    toggleUrl(){
      this.playing = !this.playing;
    },
    nextSong: function(currentSong,currentGenre,Songs){
      this.currentSong +=1;
      console.log("currentSOng: " + currentSong + " currentGenre: " + currentGenre);
      console.log("called form NEXT");

      
      this.vidoeID = Songs[currentGenre][this.currentSong];


      this.$root.$emit('changeSong', this.vidoeID);
    },
    prevSong: function(currentSong,currentGenre,Songs){
       this.currentSong -=1;
      console.log("currentSOng: " + currentSong + " currentGenre: " + currentGenre);
      console.log("called form PREV");

     
      this.vidoeID = Songs[currentGenre][this.currentSong];


      this.$root.$emit('changeSong', this.vidoeID);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
