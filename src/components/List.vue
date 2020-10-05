<template>
<div>

  <div class="list">
        <ul>
            <a href="#" id="showHide">
                <li @click="showHide()">
                    Menu
                </li>
            </a>
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
      },
      showHide: function(){
        var listItems = document.getElementsByClassName("list")[0].children[0];

        if (listItems.children[1].style.display == "true" || listItems.children[1].style.display == "") {
            for (var i=1;i<5;i++) {
                listItems.children[i].style.display = "none";
            }
            if (document.body.clientWidth < 600) {
                document.getElementsByClassName("list")[0].style.background = "none";
            }
        }
        else {
            for (i=1;i<5;i++) {
                listItems.children[i].style.display = "";
            }
            if (document.body.clientWidth < 600) {
                document.getElementsByClassName("list")[0].style.background = "#222222";
            }
        }
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

#showHide{
    color: #a7a7a7;
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
@media (max-width:599px) {
    .list{
        padding-left: 0;
        position: absolute;
        top: 45px;
        left: -35px;
    }
}
</style>
