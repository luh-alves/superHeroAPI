<template>
    <div class="logo">
        <img class="nome" src="../assets/International_Pokémon_logo.svg">
        <div class="search">
            <input id="search-input" class="input is-normal" type="text" placeholder="Search Pokémon">
            <button class="button is-light" @click="callSearch">
                <span class="icon">
                    <i class="fas fa-search"></i>
                </span>
            </button>

        </div>
    </div>
    <div class="container">
        <div class="grid-container" v-if="pokemonList.length">
            <div class="itens" v-for="pokemon in pokemonList" :key="pokemon.name" @click="onItemClick(pokemon)">{{ pokemon.name }}
            </div>
        </div>
        <div class="item error" v-if="!pokemonList.length">
            <p>No results found!</p>
        </div>
    </div>
    <DetailsModal v-if="showModal" @close="showModal = false" :poke-info="selectedPokemon"/>
</template>
  
<script lang="ts">
import { isArray } from '@vue/shared';
import { defineComponent, onMounted, ref } from 'vue';


const searchPokemons = async (query = "") => {
    try {
        const result = await fetch(`https://pokeapi.co/api/v2/pokemon/${query}`);
        const data = await result.json()
        return isArray(data.results) ? data.results : [data];
    } catch (e) {
        return []
    }
}

import DetailsModal from './DetailsModal.vue';

export default defineComponent({
    components: {
        DetailsModal
    },
    setup: () => {
        const showModal = ref(false)
        const selectedPokemon = ref({})
        const pokemonList = ref([])
        onMounted(async () => {
            pokemonList.value = await searchPokemons()
        })

        return {
            pokemonList: pokemonList,
            showModal: showModal,
            selectedPokemon: selectedPokemon
        }
    },
    methods: {
        async callSearch() {
            const query: string = (document.getElementById("search-input") as HTMLInputElement).value
            this.pokemonList = await searchPokemons(query)
        },
        onItemClick(pokemon: any) {
            this.showModal = true
            this.selectedPokemon = pokemon
        }
    },
});

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Righteous&display=swap');

.grid-container {
    width: 100%;
    display: grid;
    grid-template-columns: auto auto auto auto;
    grid-gap: 5px;

}

.itens {
    border: 0.5px solid blue;
    background-color: rgb(255, 217, 0);
    color: blue;
    text-align: center;
    padding: 0.5rem;
    font-family: 'Poppins', sans-serif;
    font-family: 'Righteous', cursive;
    font-size: 19px;
}

.logo {
    padding-top: 0.5rem;
    display: flex;
    justify-content: space-around;
    padding-bottom: 0.5rem;


}

img {
    height: 150px;
    width: 250px;
}

.search {
    padding-top: 4rem;
}

input {
    width: 400px;
    height: 35px;
}

button {
    height: 35px;
    margin-left: 1rem;
}
</style>