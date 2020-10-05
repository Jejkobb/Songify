<template>
<div>

  <div class="list">
        <ul>
            <a href="#" id="que">
                <li @click="changeGenre(0)">
               Your Queue
           </li>
            </a>
           <a href="#" id="popular">
                <li @click="changeGenre(1)">
               Popular
           </li>
           </a>
           <a href="#" id="rock">
                <li @click="changeGenre(2)">
               Rock
           </li>
           </a>
           <a href="#" id="rap">

           <li @click="changeGenre(3)">
               Rap
           </li>
           </a>
       </ul>

  </div>
</div>
</template>

<script>
export default {
  name: 'List',
  props: {
    msg: String
    
  },
  methods:{
      changeGenre: function(genre){
        this.$root.$emit('changeGenreEvent', genre);
        console.log(genre);
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li{
    font-size: 2em;
    font-family: 'Bebas Neue', cursive;
    list-style-type: none;
    position: sticky;
    margin: 1em;
}
.list{
    display: block;
    float: left;
    padding-left: 20em;

}
a:link {
    text-decoration: none;
}

a:visited {
    text-decoration: none;
    color: aliceblue;
}

a:hover {
    text-decoration: underline;
}

a:active {
    text-decoration: underline;
}
center{
    padding-left: 0em;
}

#que{
    color: #ffffff;
}
#popular{
    color: #ff7bac;
}
#rock{
    color: #7ac943;
}
#rap{
    color: #3fa9f5;
}
</style>
