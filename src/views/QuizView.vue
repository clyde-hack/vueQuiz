<script setup>
    import { useRoute } from 'vue-router';
    import { ref, computed } from 'vue'
    import q from '../data/quizes.json'
    import QuestionHeader from '../components/QuestionHeader.vue'
    import Question from '../components/Question.vue'
    import Results from '../components/Results.vue'

    const route = useRoute();
    const quiz = q.find(quiz => quiz.name.toLocaleLowerCase() === route.params.name)
    const currentQuestion = ref(0)
    const questionStatus = computed(() => `${currentQuestion.value} / ${quiz.questions.length}`)
    const questionProgress = computed(() => `${currentQuestion.value / quiz.questions.length * 100}%`)
    const correctAnswers = ref(0)
    const showResults = ref(false)

    function onOptionSelected(isCorrect) {
        if (isCorrect) {
            correctAnswers.value ++
        }

        if (quiz.questions.length - 1 === currentQuestion.value) {
            showResults.value = true
        }

        currentQuestion.value ++
    }
</script>

<template>
    <section>
        <QuestionHeader :name="quiz.name" :status="questionStatus" :progress="questionProgress" />

        <Question v-if="!showResults" :question="quiz.questions[currentQuestion]" @select-option="onOptionSelected" />

        <Results v-else="showResults" :correct-answers="correctAnswers" :quiz-length="quiz.questions.length" />
    </section>
</template>