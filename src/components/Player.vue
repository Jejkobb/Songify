<template>
  <div class="footer">
    <img id="prev" src="../assets/prev.png">
    <img v-if="!playing" @click="toggleUrl" id="play" src="../assets/play.png">
    <img v-else @click="toggleUrl" id="pause" src="../assets/pause.png">
    <img id="next" src="../assets/next.png">
  </div>
</template>

<script>
export default {
  name: 'Player',
  data() {
    return {
      playing: false
    }
  },
  methods: {
    toggleUrl(){
      this.playing = !this.playing;
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
