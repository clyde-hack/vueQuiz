<script setup>
    import { RouterView } from 'vue-router'
</script>

<template>
    <header class="main">
        <h2 class="main__title">Quizzes</h2>
    </header>

    <RouterView />
</template>

<style lang="scss">
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

    #app {
        padding: 1.5rem;
        background-color: ghostwhite;
        font-family: 'Poppins', sans-serif;

        .main {
            margin-bottom: 3rem;
            
            &__title {
                margin: 0;
                font-weight: 600;
                line-height: 1em;
            }
        }
    }
</style>
