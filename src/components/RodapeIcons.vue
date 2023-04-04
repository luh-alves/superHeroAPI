<template>
    <footer class="footer">
        <div class="content has-text-centered">
            <p>
                <strong>Feito por Luciana Alves</strong>
                <span class="icon">
                    <a href="https://www.linkedin.com/in/luciana-alves-373993ba/"><i class="fa-brands fa-linkedin"></i></a>
                    <a href="https://www.facebook.com/luciana.alves.3532507"><i class="fa-brands fa-instagram"></i></a>
                    <a href="https://github.com/luh-alves"><i class="fa-brands fa-github"></i></a>
                    <a href="https://www.facebook.com/luciana.alves.3532507"><i class="fa-brands fa-facebook"></i></a>


                </span>

            </p>
        </div>
    </footer>
</template>
<script lang="ts">
import { exportDefaultDeclaration } from '@babel/types';
import { defineComponent, DefineComponent } from 'vue';


export default defineComponent({
    name: 'RodapeIcons'
})
</script>
<style scoped>

.content{
    padding-bottom: 2rem;
    background-color: #F5A326;

;
}
.content p{
    padding-top: 2rem;
    
}
.icon a {
    text-decoration: none;
    color: black;
}
</style>