<template>
  <main class="columns is-full">
    <div class="column is-full">

      <AppHeader />
      <ListaHerois />
      <RodapeIcons />

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppHeader from './components/AppHeader.vue';
import ListaHerois from './components/ListaHerois.vue';
import RodapeIcons from './components/RodapeIcons.vue';

export default defineComponent({
  name: "App",
  components: {
    AppHeader,
    ListaHerois,
    RodapeIcons,
}
});
</script>





