<script setup>
    import { ref } from 'vue'
    import q from '../data/quizes.json'
    import Card from '../components/Card.vue'

    const quizzes = ref(q)
    const search = ref('')

    function filterQuizzes() {
        quizzes.value = q.filter(item => item.name.toLowerCase().includes(search.value.toLowerCase()))
    }
</script>

<template>
    <section>
        <header>
            <label>Search</label>
            <input type="text" v-model.trim="search" @keyup="filterQuizzes">
        </header>

        <div class="cards">
            <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
        </div>
    </section>
</template>

<style scoped lang="scss">
    header {
        margin: 1.5rem 0;

        label {
            margin-right: .5rem;
            font-size: 0.875em;
            font-weight: 500;
        }

        input {
            border: 1px solid gainsboro;
            padding: 0 .4rem;
            font-size: 1em;
            line-height: 1.75rem;
        }
    }
    .cards {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 1.5rem;
        margin: 1.5rem 0;
    }
</style>
