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
              <p>Popular låt 1</p>
            </div>
            <div class="entry">
              <p>Popular låt 2</p>
            </div>
            </div>
            <div v-show="this.genre == 2">
              <div class="entry odd">
              <p>Rock låt 1</p>
            </div>
            <div class="entry">
              <p>Rock låt 2</p>
            </div>
            </div>
            <div v-show="this.genre == 3">
              <div class="entry odd">
              <p>Rap låt 1</p>
            </div>
            <div class="entry">
              <p>Rap låt 2</p>
            </div>
            </div>
          </center>
    
  </div>
</template>

<script>

export default {
  name: 'Paster',
  props:{
    genre: Number
  },
  methods: {
    paste(e){
      var item = document.createElement("div");
      if(document.getElementsByClassName("entry").length % 2 == 0){
        item.classList.add("odd");
      }
      item.classList.add("entry");
      item.innerHTML = e.target.value;
      document.getElementById("wrapper").prepend(item);
      e.target.value = "";
     
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
</style>
