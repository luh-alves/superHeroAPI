<template>
    <footer>
        <div class="container">
            <div class="item"><strong>Feito por Luciana Alves</strong></div>
            <div class="item"><a href="https://www.linkedin.com/in/luciana-alves-373993ba/"><i
                        class="fa-brands fa-linkedin"></i></a></div>
            <div class="item"><a href="https://www.facebook.com/luciana.alves.3532507"><i
                        class="fa-brands fa-instagram"></i></a></div>
            <div class="item"><a href="https://github.com/luh-alves"><i class="fa-brands fa-github"></i></a></div>
            <div class="item"><a href="https://www.facebook.com/luciana.alves.3532507"><i
                        class="fa-brands fa-facebook"></i></a></div>

        </div>
    </footer>
</template>
<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent({
    name: 'RodapeIcons'
})
</script>
<style scoped>
.container {
    display: flex;
    justify-content: center;
}

.item {
    padding-top: 5rem;
    padding-left: 1rem;
}

a {
    text-decoration: none;
    color: black;
}
</style>
