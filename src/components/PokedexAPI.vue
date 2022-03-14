<template>
  <div class="wrapper">
      <h1>POKEDEX</h1>
      <div class="button-container">
        <button @click="fetchPokemon('normal')" class="button normal">NORMAL</button>
        <button @click="fetchPokemon('fighting')" class="button fighting">FIGHTING</button>
        <button @click="fetchPokemon('flying')" class="button flying">FLYING</button>
        <button @click="fetchPokemon('poison')" class="button poison">POISON</button>
        <button @click="fetchPokemon('ground')" class="button ground">GROUND</button>
        <button @click="fetchPokemon('rock')" class="button rock">ROCK</button>
        <button @click="fetchPokemon('bug')" class="button bug">BUG</button>
        <button @click="fetchPokemon('ghost')" class="button ghost">GHOST</button>
        <button @click="fetchPokemon('steel')" class="button steel">STEEL</button>
        <button @click="fetchPokemon('fire')" class="button fire">FIRE</button>
        <button @click="fetchPokemon('water')" class="button water">WATER</button>
        <button @click="fetchPokemon('grass')" class="button grass">GRASS</button>
        <button @click="fetchPokemon('electric')" class="button electric">ELECTRIC</button>
        <button @click="fetchPokemon('psychic')" class="button psychic">PSYCHIC</button>
        <button @click="fetchPokemon('ice')" class="button ice">ICE</button>
        <button @click="fetchPokemon('dragon')" class="button dragon">DRAGON</button>
        <button @click="fetchPokemon('dark')" class="button dark">DARK</button>
        <button @click="fetchPokemon('fairy')" class="button fairy">FAIRY</button>

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
          //Creates array 'promises' and pushes on to promises the json object for every pokemon
          const promises = [];
          for (let i = 1; i <= 150; i++) {
              const url = 'https://pokeapi.co/api/v2/pokemon/'+ i;
              promises.push(fetch(url)
              .then((res) => res.json()));
          }
          
          //Uses higher order map function to create a new array 'pokemon' and push a few data objects to it
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

          //Filters pokemon of specific type
          const filterPokemon = (pokemons, pokemonType) => {
              const filteredPokemon = pokemons.filter((pokemon) => pokemon.type == pokemonType);
              console.log(pokemons);                
              console.log(pokemonType);
              console.log(filteredPokemon);
              displayPokemon(filteredPokemon)
          };

          //Displays filtered pokemon
          const displayPokemon = (filteredPokemon) => {
            const pokemonHTMLString = filteredPokemon
                .map(
                (filteredPokeman) => 
                `
                    <li class="card">
                        <img class="card-image" src="${filteredPokeman.backImage}"/>
                        <h2 class="card-title">${filteredPokeman.id}. ${filteredPokeman.name}</h2>
                        <p class="card-subtitle">Type: ${filteredPokeman.type}</p>
                    </li>
                `
                )
                .join('');
                console.log(pokemonHTMLString);
                this.pokedex = pokemonHTMLString;
          };
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

    .ground {
        background-color: white;
        color: black;
        border: 2px solid #EECC55;
        border-radius: 5px;
    }
    .ground:hover {background-color: #EECC55;}

    .rock {
        background-color: white;
        color: black;
        border: 2px solid #CCBD72;
        border-radius: 5px;
    }
    .rock:hover {background-color: #CCBD72;}

    .bug {
        background-color: white;
        color: black;
        border: 2px solid #C2D21E;
        border-radius: 5px;
    }
    .bug:hover {background-color: #C2D21E;}

    .ghost {
        background-color: white;
        color: black;
        border: 2px solid #7975D7;
        border-radius: 5px;
    }
    .ghost:hover {background-color: #7975D7;}

    .steel {
        background-color: white;
        color: black;
        border: 2px solid #C4C2DB;
        border-radius: 5px;
    }
    .steel:hover {background-color: #C4C2DB;}

    .fire {
        background-color: white;
        color: black;
        border: 2px solid #FA5643;
        border-radius: 5px;
    }
    .fire:hover {background-color: #FA5643;}

    .water {
        background-color: white;
        color: black;
        border: 2px solid #56ADFF;
        border-radius: 5px;
    }
    .water:hover {background-color: #56ADFF;}

    .grass {
        background-color: white;
        color: black;
        border: 2px solid #8CD750;
        border-radius: 5px;
    }
    .grass:hover {background-color: #8CD750;}

    .electric {
        background-color: white;
        color: black;
        border: 2px solid #FDE139;
        border-radius: 5px;
    }
    .electric:hover {background-color: #FDE139;}

    .psychic {
        background-color: white;
        color: black;
        border: 2px solid #FA65B4;
        border-radius: 5px;
    }
    .psychic:hover {background-color: #FA65B4;}

    .ice {
        background-color: white;
        color: black;
        border: 2px solid #96F1FF;
        border-radius: 5px;
    }
    .ice:hover {background-color: #96F1FF;}

    .dragon {
        background-color: white;
        color: black;
        border: 2px solid #8673FF;
        border-radius: 5px;
    }
    .dragon:hover {background-color: #8673FF;}

    .dark {
        background-color: white;
        color: black;
        border: 2px solid #8D6855;
        border-radius: 5px;
    }
    .dark:hover {background-color: #8D6855;}

    .fairy {
        background-color: white;
        color: black;
        border: 2px solid #F9AEFF;
        border-radius: 5px;
    }
    .fairy:hover {background-color: #F9AEFF;}


</style>