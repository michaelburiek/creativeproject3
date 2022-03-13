<template>
    <div class="wrapper">
      <div class="image-container">
        <img v-bind:src="img" alt="Pokemon Map" class="image">
      </div>
      <div class="footer">
        <a href="https://github.com/michaelburiek/creativeproject3.git"><b>GITHUB</b></a>
      </div>
    </div>
</template>

<script>

export default {
  name: 'PokemonMap',
  data() {
    return {
      img: require("../assets/pokemonmap.jpeg")
    }
  }
}
</script>

<style scoped>
  .wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  .image-container {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .image {
    display: flex;
    border-radius: 10px;
  }
  .footer a{
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 10px;
    height: 50px;
    text-decoration: none;
    color: black;
  }

</style>