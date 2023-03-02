<script setup>
    import { RouterLink } from 'vue-router';

    const { quiz } = defineProps(['quiz'])
</script>

<template>
    <RouterLink :to="`/quiz/${quiz.name.toLowerCase()}`" class="card">
        <img :src="quiz.img" alt="Card Image" class="card__img">
        <h4 class="card__title">{{ quiz.name }}</h4>
        <p class="card__text">{{ quiz.questions.length }} Questions</p>
    </RouterLink>
</template>

<style scoped lang="scss">
    .card {
        display: flex;
        flex-direction: column;
        background-color: white;
        box-shadow: 0 0 8px rgba(black, .08);
        text-decoration: none;
        color: inherit;

        &__img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        &__title {
            margin: 0 .75rem;
            font-weight: 500;
            line-height: 2rem;
        }

        &__text {
            margin: 0 .75rem;
            font-size: 0.875em;
            line-height: 2rem;
        }
    }
</style>