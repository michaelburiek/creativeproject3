<template>
  <h1>POKEDEX</h1>
  <button @click="fetchPokemon()" class="button button1">Pokemon</button>
  <p>{{pokemon}}</p>
</template>

<script>
export default {
  name: 'PokedexAPI',
  data: function() {
    return {
      apiUrl: 'https://pokeapi.co/api/v2/pokemon/1',
      pokemon: [],
    }
  },
  mounted() {
      let req = new Request(this.apiUrl);
      fetch(req)
        .then((resp) => {
          if(resp.status === 200)
            return resp.json()
        })
        .then((data) => {
          this.pokemon = data.results
          console.log(this.pokemon)
        })
        .catch((error) => {
            console.log(error.message);
        })
  },
}
</script>

<style scoped>
    .button {
        background-color: white;
        border: none;
        color: white;
        text-align: center;
        text-decoration: none;
        display: inline-flex;
        margin: 4px 2px;
        font-size: 16px;
        transition-duration: 0.4s;
        cursor: pointer;
    }
    .button1 {
        background-color: white;
        color: black;
        border: 2px solid #e7e7e7;
    }
    .button1:hover {background-color: #e7e7e7;}
</style>