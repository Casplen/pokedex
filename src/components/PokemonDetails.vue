<template>
  <div class="pokedex-card">
      <header>
        <h3>
          #{{pokemon.id}}: {{pokemon.name[0].toUpperCase() + pokemon.name.substring(1)}}
        </h3>
      </header>
      <hr>
      <div class="sprite-container">
        <img :src="pokemon.sprites.front_default" alt="">
      </div>
      <hr>
      <div class="type-container">
        <p v-for="type in pokemon.types" :key=type.slot :class="typeClass(type.type.name)">{{type.type.name[0].toUpperCase() + type.type.name.substring(1)}}</p>
      </div>
  </div>
</template>

<script>
export default {
    name: 'pokemon-details',
    props: [ 'pokemon' ],
    methods: {
      typeClass(type) {
        let className = "default";
        let typeList = ["normal", "water", "electric", "fighting", "ground", "psychic", "rock", "dark", "steel", "fire", "grass", "ice", "poison", "flying", "bug", "ghost", "dragon", "fairy"]
        typeList.forEach(typeClass => {
          if (typeClass === type) {
            className = typeClass
          }
        })
        return className
      }
    }

}
</script>

<style scoped>

hr {
  border: 1px solid rgb(199, 199, 199);
  width: 90%;
}

h3 {
  margin: 10px;
  font-size: 1em;
}

.pokedex-card{
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 10px;
  padding: 10px;
  border: 1px solid rgb(199, 199, 199);
  width: 300px;
  background-color: white;
}

.type-container {
  display: flex;
  flex-wrap: wrap;
}

.type-container > p {
  margin: 5px;
  padding: 5px;
  border: 1px solid grey;
  color: white;
  font-size: 0.8em;
}

.normal {
  background-color: #A8A77A;
}
.water {
  background-color: #6390F0;
}
.electric {
  background-color: #F7D02C;
}
.fighting {
  background-color: #C22E28;
}
.ground {
  background-color: #E2BF65;
}
.psychic {
  background-color: #F95587;
}
.rock {
  background-color: #B6A136;
}
.dark {
  background-color: #705746;
}
.steel {
  background-color: #B7B7CE;
}
.fire {
  background-color: #EE8130;
}
.grass {
  background-color: #7AC74C;
}
.ice {
  background-color: #96D9D6;
}
.poison {
  background-color: #A33EA1;
}
.flying {
  background-color: #A98FF3;
}
.bug {
  background-color: #A6B91A;
}
.ghost {
  background-color: #735797;
}
.dragon {
  background-color: #6F35FC;
}
.fairy {
  background-color: #D685AD;
}

</style>