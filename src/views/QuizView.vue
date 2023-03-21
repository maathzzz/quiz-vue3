<script setup>
    import { ref, watch } from "vue";
    import { useRoute } from "vue-router"; 
    import Question from "../components/Question.vue";
    import QuizHeader from "../components/QuizHeader.vue";
    import quizes from "../data/quizes.json";


    const route = useRoute()
    const quizId = parseInt(route.params.id)

    const quiz = quizes.find(q => q.id === quizId)
    const currentQuestionIndex = ref(0)

    watch(() => currentQuestionIndex.value, () => {
        console.log('current')
    })

    // 5:34:00

    const questionStatus = `${currentQuestionIndex.value}/${quiz.questions.length}`
</script>

<template>
    <div>
        <QuizHeader :questionStatus="questionStatus"/>
        <div>
            <Question :question="quiz.questions[currentQuestionIndex]"/>
        </div>
        <button @click="currentQuestionIndex++"> Next </button>
    </div>
</template>

<style scoped>

</style>