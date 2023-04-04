<template>
  <main class="columns is-full">
    <div class="column is-full">
      
      <BarraLateral/>
      <CardsItens/>
      <RodapeIcons/>

    </div>
    


  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import CardsItens from './components/CardsItens.vue';
import RodapeIcons from './components/RodapeIcons.vue';
export default defineComponent({
  name: "App",
  components: { BarraLateral, CardsItens, RodapeIcons },
  
});
</script>

<style></style>
