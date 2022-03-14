<template>
  <div class="wrapper">
      <h1>POKEDEX</h1>
      <div class="button-container">
        <button @click="fetchPokemon('normal')" class="button normal">NORMAL</button>
        <button @click="fetchPokemon('fighting')" class="button fighting">FIGHTING</button>
        <button @click="fetchPokemon('flying')" class="button flying">FLYING</button>
        <button @click="fetchPokemon('poison')" class="button poison">POISON</button>
      </div>

      <div class="pokedex-container">
        <ul>{{pokedex}}</ul>
      </div>

      <div class="footer-container">
        <a href="https://github.com/michaelburiek/creativeproject3.git"><b>GITHUB</b></a>
      </div>
  </div>
</template>

<script>
export default {
  name: 'PokedexAPI',
  data() {
    return {
        pokedex: '',
    }
  },
  methods: {
      fetchPokemon(pokemonType) {
          
          //Filters pokemon of specific type
          const filterPokemon = (pokemon, pokemonType) => {
              const filteredPokemon = [];
              console.log(pokemon);
              console.log(pokemonType);
              console.log(filteredPokemon);
              
              

          };
          
        
          //Creates array 'promises' and pushes on to promises the json object for every pokemon
          const promises = [];
          for (let i = 1; i <= 150; i++) {
              const url = 'https://pokeapi.co/api/v2/pokemon/'+ i;
              promises.push(fetch(url)
              .then((res) => res.json()));
          }
          
          //
          Promise.all(promises).then((results) => {
              const pokemon = results.map((result) => ({
                  name: result.name,
                  backImage: result.sprites['back_default'],
                  frontImage: result.sprites['front_default'],
                  type: result.types[0].type.name,
                  id: result.id,
              }));
              filterPokemon(pokemon, pokemonType)
          });
      },
  },
}
</script>

<style scoped>
    .pokedex-container {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100vh;
        border: solid;
        border-radius: 10px;
        margin: 20px;
    }
    .footer-container a{
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 10px;
        height: 50px;
        text-decoration: none;
        color: black;
    }
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
    .normal {
        background-color: white;
        color: black;
        border: 2px solid #BABAAE;
        border-radius: 5px;
    }
    .normal:hover {background-color: #BABAAE;}

    .fighting {
        background-color: white;
        color: black;
        border: 2px solid #A75543;
        border-radius: 5px;
    }
    .fighting:hover {background-color: #A75543;}

    .flying {
        background-color: white;
        color: black;
        border: 2px solid #78A2FF;
        border-radius: 5px;
    }
    .flying:hover {background-color: #78A2FF;}

    .poison {
        background-color: white;
        color: black;
        border: 2px solid #A95CA0;
        border-radius: 5px;
    }
    .poison:hover {background-color: #A95CA0;}
</style>