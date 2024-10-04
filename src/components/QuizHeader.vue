<script setup>
import { defineProps } from "vue";
const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
</script>

<template>
  <header class="quiz__header">
    <h4>Question {{ questionStatus }}</h4>
    <div class="quiz__bar">
      <div class="quiz__completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
h4 {
  font-size: 30px;
}
.quiz__completion {
  height: 100%;
  width: 0%;
  background-color: #68753e;
}

.quiz__bar {
  width: 300px;
  height: 50px;
  border: 1px solid #68753e;
}

.quiz__header {
  margin-top: 20px;
}
</style>
