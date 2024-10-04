<script setup>
import { defineProps, defineEmits } from "vue";
const { question } = defineProps(["question"]);
const emit = defineEmits(["selectOption"]);
const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>

<template>
  <div class="question__container">
    <h1 class="question__title">
      {{ question.text }}
    </h1>
  </div>
  <div class="option__container">
    <div
      v-for="option in question.options"
      :key="option.id"
      class="option"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="option__label">{{ option.label }}</p>
      <div class="option__value">
        <p>{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.option__value {
  background-color: rgb(109, 114, 108);
  width: 100%;
  font-size: 25px;
  padding: 0 20px;
}

.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}

.option__label {
  display: flex;
  background-color: #68753e;
  height: 50px;
  font-size: 30px;
  width: 60px;
  justify-content: center;
  align-items: center;
}

.question__container {
  margin-top: 20px;
}

.question__title {
  font-size: 40px;
  margin-bottom: 20px;
}
</style>
