<script setup>
    // useRoute is used to get information
    // useRouter is used to modify and mutate
    import { useRouter } from "vue-router";

    const router = useRouter()
    const {quiz} = defineProps(['quiz'])

    const navigateToQuiz = () =>{
      router.push(`/quiz/${quiz.id}`)
    }

</script>

<template>
    <div class="card" @click="navigateToQuiz">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2> {{ quiz.name }} </h2>
          <p> {{ quiz.questions.length }} questions</p>
        </div>
      </div>
</template>

<style scoped>
     /* CARD */
  .card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 10px 1px 15px 10px rgba(0,0,0,0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
    transition: transform 600ms;
  }

  .card:active{
    transform: scale(0.88);
  }

  .card img{
    width: 100%;
    height: 190px;
    margin: 0;
  }

  .card .card-text{
    padding: 0 5px;
  }

  .card .card-text h2 {
    font-weight: bold;
  }
</style>