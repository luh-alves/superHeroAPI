<template>
    <header>

    </header>
</template>
<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent({
    name: 'AppHeader'
})

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

header {
    padding: auto;
    padding-top: 1.5rem;
    padding-bottom: 1rem;
    background-image: url("../assets/landscape-1456483171-pokemon2.jpg");
    flex-direction: row;
    height: 220px;
}



@media only screen and (max-width:768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>