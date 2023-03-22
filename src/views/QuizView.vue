<script setup>
    import { ref, watch, computed } from "vue";
    import { useRoute } from "vue-router"; 
    import Question from "../components/Question.vue";
    import QuizHeader from "../components/QuizHeader.vue";
    import quizzes from "../data/quizes.json";


    const route = useRoute();
    const quizId = parseInt(route.params.id);

    const quiz = quizzes.find(q => q.id === quizId);
    const currentQuestionIndex = ref(0);

    // const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`);

    // watch(() => currentQuestionIndex.value, () => {
    //     questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`;
    // })

    // computed() serve para computar uma variável que funcione a base de outra variável

    const questionStatus = computed(() => {
        return `${currentQuestionIndex.value}/${quiz.questions.length}`;
    })

    const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)

    // 05:40:00

</script>

<template>
    <div>
        <!-- passando propriedades, a primeira vai ser chamada no componente a segunda é equidade nesta view -->
        <QuizHeader 
            :questionStatus="questionStatus"
            :barPercentage="barPercentage"
        />
        <div>
            <Question :question="quiz.questions[currentQuestionIndex]"/>
        </div>
        <button @click="currentQuestionIndex++"> Next </button>
    </div>
</template>

<style scoped>

</style>