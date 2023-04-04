<template>
    <header>
        <h1>SuperHeroAPI</h1>
        <div class="search is-flex-direction-row">
            <input class="input is-normal" type="text" placeholder="Search Super Hero">
            <button class="button is-light">
                <span class="icon">
                    <i class="fas fa-search"></i>
                </span>
            </button>

        </div>

    </header>
</template>
<script lang="ts">
import { exportDefaultDeclaration } from '@babel/types';
import { defineComponent, DefineComponent } from 'vue';


export default defineComponent({
    name: 'BarraLateral'
})

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

header {
    padding: auto;
    padding-top: 1.5rem;
    padding-bottom: 1rem;
    background-image: url("../assets/logo2.avif");
    flex-direction: row;



}

.search {
    padding-left: 45rem;
    justify-content: space-around
}


input {
    width: 400px;
    height: 35px;
}

button {
    height: 35px;
    margin-left: 1rem;
}

h1 {
    color: #160b30;
    font-size: 25px;
    font-weight: bold;
    font-family: 'Righteous', cursive;
    padding-left: 12rem;

}

@media only screen and (max-width:768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>