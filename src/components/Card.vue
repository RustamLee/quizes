<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const { quiz } = defineProps(["quiz"]);

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" class="card__image" />
    <div class="card__title">
      <h2 class="card__subtitle">{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}

.card__image {
  width: 100%;
  height: 190px;
  margin: 0;
}

.card__title {
  padding: 0 5px;
}

.card__subtitle {
  font-weight: bold;
}
</style>
