<template>
  <div class="modal-mask">
    <div class="modal-wrapper">
      <div class="modal-container">
        <div class="modal-body">
          <slot name="body">
            <div class="container">
              <div class="tile is-ancestor">
                <div class="tile is-parent">
                  <article class=" card tile is-child box">
                    <div class="containerConteudo is-flex-direction-column">
                      <img :src="pokemon.sprites?.front_default">
                      <p class="title">{{ pokemon.name }}</p>
                      <p class="subtitle">{{ getTypes(pokemon) }}</p>
                      <div class="teste">
                        <h4>Abilities</h4>
                        <div class="informacoesHeros">
                          <p v-for="ability in getAbilities(pokemon)" :key="ability.name">{{ ability.name }}</p>
                        </div>
                      </div>
                    </div>
                  </article>
                </div>
              </div>
            </div>
          </slot>
        </div>

        <div class="modal-footer">
          <slot name="footer">
            <button class="modal-default-button" @click="$emit('close')">
              OK
            </button>
          </slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">

import { defineComponent, ref } from 'vue';
import axios from "axios";


const getPokemon = async (url: string) => {
  const result = await axios.get(url);
  const data = await result.data
  return data;
}
export default defineComponent({
  name: 'DetailsModal',
  props: ["pokeInfo"],
  setup() {
    return {
      pokemon: ref({} as any)
    }
  },
  async mounted() {
    if (this.pokeInfo.url) {
      this.pokemon = await getPokemon(this.pokeInfo.url)
    } else {
      this.pokemon = this.pokeInfo
    }

  },
  methods: {
    getTypes(pokemon: any) {
      return pokemon.types?.map((type: any) => type.type.name).join(", ")
    },
    getAbilities(pokemon: any) {
      return pokemon.abilities?.map((ability: any) => ability.ability)
    }
  }
})
</script>


<style>
.card {

  border: 1px solid blue;
  background-color: rgb(255, 217, 0);
  color: blue;

}

.containerConteudo {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: aliceblue;
}

h4 {
  font-size: 25px;
  color: #160b30;
  font-family: 'Righteous', cursive;
  border-bottom: blue;
}

button {
  font-family: 'Righteous', cursive;

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

  color: blue;
  transform: translateX(10px) scale(1.2);
  border-bottom: 1px solid;
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 500px;
  margin: 0px auto;
  padding: 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-default-button {
  margin-top: 20px;
}
</style>