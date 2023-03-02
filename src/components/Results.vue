<script setup>
    import { defineProps } from 'vue';

    const { correctAnswers, quizLength } = defineProps(['correctAnswers', 'quizLength'])

    const result = `${correctAnswers} / ${quizLength}`
</script>

<template>
    <div class="results">
        <h3>Your Results&hellip;</h3>

        <h1>{{ result }}</h1>

        <RouterLink to="/">Go Back</RouterLink>
    </div>
</template>

<style scoped lang="scss">
    .results {
        padding: 8rem;
        text-align: center;
    }

    h3 {
        font-weight: 400;
    }

    h1 {
        font-weight: 500;
    }

    a {
        color: steelblue;
    }
</style>