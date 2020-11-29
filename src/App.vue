<template>
  <div id="app">
    <header>
      <h1>Pokedex</h1>
    </header>
    <div class="search">
      <p>&#9654</p>
      <input type="text" v-model="searchTerm" placeholder="Search...">
    </div>
    <div id="pokedex">
      <pokemon-details v-for="pokemon in filteredPokemon" :key="pokemon.id" :pokemon="pokemon"></pokemon-details>
    </div>
  </div>
</template>

<script>
import PokemonDetails from './components/PokemonDetails.vue'

export default {
  name: "app",
  data(){
    return {
      pokemonList: [],
      searchTerm: ""
    }
  },
  mounted(){
    this.getPokemon()
    this.sortPokemon()

  },

  computed:{
    filteredPokemon(){
            return this.pokemonList.filter((pokemon) => pokemon.name.includes(this.searchTerm.toLowerCase()))
        }
  },

  methods: {
    getPokemon: function() {
      fetch("https://pokeapi.co/api/v2/pokemon?limit=151")
      .then(res => res.json())
      .then(data => data.results.forEach(pokemon => this.getPokemonData(pokemon))
      )
    },
    getPokemonData: function(pokemon) {
      fetch(pokemon.url)
      .then(res => res.json())
      .then(data => this.pokemonList.push(data))
    },
    sortPokemon: function() {
      let sortedPokemon = this.pokemonList.sort(function(a, b){
        return a[id] < b[id] ? -1 : 1
      })
      return sortedPokemon = this.pokemonList
    }
  },
  components: {
    "pokemon-details": PokemonDetails
  }

}
</script>

<style scoped>
#app {
  font-family: 'Press Start 2P', cursive;
}

#pokedex {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin: 10px;
  justify-content: center;
}

header {
  background-color: #f73333;
  padding: 10px;
  color: white;
  border-bottom: 5px solid black;
}

.search {
  display: flex;
  background-color: white;
  padding: 3px;
  border-bottom: 2px solid rgb(199, 199, 199);
  padding-left: 5%
}

.search > input {
  border: none;
  padding-left: 15px;
  margin-left: 15px;
  width: 400px;
  font-size: large;
  font-family: helvetica;
  font-weight: bold;
}
h1{
  padding: 20px;
  margin: 0px;
}
</style>