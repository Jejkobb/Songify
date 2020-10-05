<template>
  <div class="footer">
    <h2>
      Now playing: {{songTitle}}
    </h2>
    <img id="prev" @click="prevSong(currentSong,genre,Songs)" src="../assets/prev.png">
    <img v-if="!playing" @click="toggleUrl" id="play" src="../assets/play.png">
    <img v-else @click="toggleUrl" id="pause" src="../assets/pause.png">
    <img id="next" @click="nextSong(currentSong,genre,Songs)" src="../assets/next.png">
  </div>
</template>

<script>
var getYoutubeTitle = require('get-youtube-title')
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
      songTitle: "Title",
      Songs: [
        ["4NRXx6U8ABQ","GrAchTdepsU","YH9Nwa0RvO8","l0U7SxXHkPY"], //your que
        ["UNZqm3dxd2w","xpVfcZ0ZcFM","DRS_PpOrUZ4","U9BwWKXjVaI"], //popular
        ["SLsTskih7_I","UceaB4D0jpo","ba7mB8oueCY","ApXoWvfEYVU"], //rock
        ["w2Ov5jzm3j8","r_0JjYUe5jo","8CdcCD5V-d8","NQbkGDoD7B0"]  // rap
      ],
      customList: []
    }
  },
  methods: {
    toggleUrl(){
      this.playing = !this.playing;
    },
    nextSong: function(currentSong,currentGenre,Songs){
      this.currentSong +=1;

      
      this.vidoeID = Songs[currentGenre][this.currentSong];


      this.$root.$emit('changeSong', this.vidoeID);
      this.getTitle(this.vidoeID);
    },
    prevSong: function(currentSong,currentGenre,Songs){
       this.currentSong -=1;

     
      this.vidoeID = Songs[currentGenre][this.currentSong];


      this.$root.$emit('changeSong', this.vidoeID);
      this.getTitle(this.vidoeID);
    },
    getTitle: function (vidoeID){
      //TODO

        getYoutubeTitle(vidoeID, function (err, title) {
             //Läser in video titeln men skriver inte ut
             

              //alert(title); <-- fungerar och visar rätt låt
              console.log("Detta är titteln: " + title);
              
            })
     
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
h2{
  display: flex;
}
</style>
