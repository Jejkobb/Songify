<template>
  <div class="main">
    <img class="logo" src="../assets/logo.png">
    <h1 class="text">{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String,
    logo: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.logo {
  width: 28px;
  margin-right: 10px;
}
.text {
  display:inline-block;
}

/* Responsivity */
@media (max-width:599px) {
  .logo {
    top: 0px;
    width: 28px;
  }
  .text {
    font-size: 200%;
  }
}
</style>
