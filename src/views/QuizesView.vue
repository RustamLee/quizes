<script setup>
import q from "../data/quizes.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";

const quizes = ref(q);
const search = ref("");

watch(search, () => {
  quizes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>
<template>
  <div>
    <header class="header">
      <h1 class="header__title">Quizes</h1>
      <input
        v-model.trim="search"
        type="text"
        class="header__input"
        placeholder="Search..."
      />
    </header>
    <div class="options__container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>
<style scoped>
.options__container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}

.header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

.header__title {
  font-weight: bold;
  margin-right: 30px;
}
.header__input {
  border: none;
  background-color: rgba(243, 237, 237, 0.1);
  padding: 10px;
  border-radius: 5px;
  color: rgb(149, 147, 147);
}
</style>
