<template>
  <div>
    <center>
    <div v-show="this.genre == 0" id="input">


      <input @change="paste" type="text" placeholder="Paste YouTube URL here...">
      
    
    <center id="wrapper">

    </center>
    </div>
    
          
            <div v-show="this.genre == 1">
              <div class="entry odd">
              <p>Drake - Nice For What</p>
            </div>
            <div class="entry">
              <p>Roddy Ricch - The Box [Official Music Video]</p>
            </div>
            <div class="entry odd">
              <p>Drake - God's Plan</p>
            </div>
            <div class="entry">
              <p>Drake - In My Feelings</p>
            </div>
            </div>
            <div v-show="this.genre == 2">
              <div class="entry odd">
              <p>Post Malone, Swae Lee - Sunflower (Spider-Man: Into the Spider-Verse)</p>
            </div>
            <div class="entry">
              <p>Post Malone - White Iverson</p>
            </div>
            <div class="entry odd">
              <p>Post Malone - rockstar ft. 21 Savage</p>
            </div>
            <div class="entry">
              <p>Post Malone - "Goodbyes" ft. Young Thug (Rated R)</p>
            </div>
            </div>
            <div v-show="this.genre == 3">
              <div class="entry odd">
              <p>SICKO MODE</p>
            </div>
            <div class="entry">
              <p>Lil Nas X - Old Town Road (Official Movie) ft. Billy Ray Cyrus</p>
            </div>
            <div class="entry odd">
              <p>Eminem - Godzilla ft. Juice WRLD (Dir. by @_ColeBennett_)</p>
            </div>
            <div class="entry">
              <p>Eminem - Venom</p>
            </div>
            </div>
          </center>
    
  </div>
</template>

<script>
var getYoutubeTitle = require('get-youtube-title')
export default {
  name: 'Paster',
  props:{
    genre: Number,
  },
  methods: {
    changeTitle(title){
      this.songTitle = title;
    },
    paste(e){
      var tmpString  ="";
      var item = document.createElement("div");
      if(document.getElementsByClassName("entry").length % 2 == 0){
        item.classList.add("odd");
      }
      item.classList.add("entry");
      item.innerHTML = e.target.value;
      document.getElementById("wrapper").prepend(item);
      tmpString = e.target.value.slice(32,45);
      console.log("tmpString: " + tmpString);
      console.log(e.value);
      e.target.value = "";
      getYoutubeTitle(tmpString, (e, t) => {
        item.innerHTML = t;
      });

      this.$root.$emit('changeSong', tmpString);

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
input {
  padding: 10px;
  width: 512px;
  text-align: center;
  color: aliceblue;
  background-color: #222;
  border-radius: 10px;
  border: solid 3px #111;
  margin-bottom: 4px;
  margin-right: 35em;
}
input:focus{
  outline: 0;
}
.entry {
  text-align: center;
  width: 512px;
  padding: 10px;
  background-color: #222;
}
.odd {
  background-color: #252525;
}
@media (max-width:599px) {
  input {
    width: 93%;
    margin-right: 0;
  }
  .entry {
    width: 93%;
  }
}
</style>
