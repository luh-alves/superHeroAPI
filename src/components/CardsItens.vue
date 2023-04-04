

<template>
  <div class="container">
    <div class="tile is-ancestor">
      <div class="tile is-parent" v-for="pokemon in pokemonList" :key="pokemon.name">
        <article class=" card tile is-child box" >
          <div class="containerConteudo is-flex-direction-column">
            <img src="../assets/logo.jpg">
            <p class="title">{{pokemon.name}}</p>
            <p class="subtitle">SUPER PODER</p>
            <div class="informacoesHeros">
              <p>informaçoes heroi:poder</p>
              <p>informaçoes heroi:poder</p>
              <p>informaçoes heroi:poder</p>
              <p>informaçoes heroi:poder</p>
              <p>informaçoes heroi:poder</p>
            </div>
          </div>
        </article>
      </div>
    </div>
  </div>
</template>
<script lang="ts">

const getPokemons = () => {
  return fetch("https://pokeapi.co/api/v2/pokemon").then(result=> result.json())
}

import { defineComponent, onMounted, ref } from 'vue';


export default defineComponent({
  name: 'CardsItens',
  setup: ()=>{
    const pokemonList = ref([])
    const fetcPokemonList = async ()=>{
      const heroes = await getPokemons();
      pokemonList.value = heroes.results.reverse().slice(0,3)
    }

    onMounted(fetcPokemonList)

    return {
      pokemonList,
    }
  }
})
</script>

<style>
.container {
  padding-top: 3rem;
  display: flex;
  flex-wrap: wrap;
}

.card {
  background-color: rgb(255, 175, 0);

}

img {
  border-radius: 50%;
  width: 160px;
}

.containerConteudo {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.informacoesHeros:hover {
  background-image: linear-gradient(to bottom right, rgba(255, 145, 0, 0.253), white);
  border-radius: 10px;
}

.informacoesHeros {
  font-family: 'Righteous', cursive;
}

.title {
  color: #160b30;
  font-size: 25px;
  font-weight: bold;
  font-family: 'Righteous', cursive;

}

.subtitle {
  color: #160b30;
  transition: transform 1s;
  transform: translateX(0) scale(0.5);
  font-size: 20px;
  font-weight: bold;
  font-family: 'Righteous', cursive;
}

.subtitle:hover,
.subtitle:focus {
  background-image: linear-gradient(to bottom right, rgba(255, 145, 0, 0.253), white);
  color: #FA2E25;
  transform: translateX(10px) scale(1.2);
  border-radius: 4px;
}
</style>