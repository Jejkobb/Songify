<template>
  <div>
    <input @change="paste" type="text" placeholder="Paste YouTube URL here...">
    <center id="wrapper">

    </center>
  </div>
</template>

<script>
export default {
  name: 'Paster',
  methods: {
    paste(e){
      var item = document.createElement("div");
      if(document.getElementsByClassName("entry").length % 2 == 0){
        console.log("hello");
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
