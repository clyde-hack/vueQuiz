<script setup>
    import { defineProps } from 'vue';

    const emit = defineEmits(['selectOption'])
    const { question } = defineProps(['question'])

    function selectOption(isCorrect) {
        emit('selectOption', isCorrect)
    }
</script>

<template>
    <div class="question">
        <h4 class="question__title">{{ question.text }}</h4>

        <div class="option" v-for="option in question.options" :key="option.id">
            <div class="option__selector" @click="selectOption(option.isCorrect)">{{ option.label }}</div>
            <div class="option__text">{{ option.text }}</div>
        </div>
    </div>
</template>

<style scoped lang="scss">
    .question {
        margin: 1.5rem 0;

        &__title {
            margin: 1.5rem 0;
            font-size: 2rem;
            font-weight: 500;
            line-height: 1em;
        }
    }

    .option {
        display: flex;
        align-items: center;
        margin: 0.5rem 0;
        background-color: white;

        &__selector {
            width: 3rem;
            height: 3rem;
            background-color: burlywood;
            cursor: pointer;
            text-align: center;
            font-size: 1.25rem;
            line-height: 3rem;
            transition: background-color 0.24s ease;

            &:hover {
                background-color: lighten(burlywood, 8);
            }
        }

        &__text {
            padding: 0 1.5rem;
        }
    }
</style>