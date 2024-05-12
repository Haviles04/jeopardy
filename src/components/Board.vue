<template>
  <div class="board">
    <div class="category" v-for="category in categories" :key="category">
      <div>
        <h1>{{ category.name }}</h1>
      </div>
      <QuestionBox v-for="question in category.questions" :key="question.id" :question="question" />
    </div>
  </div>
</template>

<script setup>
import QuestionBox from '@/components/QuestionBox.vue'
import { categories } from '../../Questions.json'
</script>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  align-items: end;
  justify-content: center;
  text-wrap: wrap;
  height: auto;
  padding: 0px 10px;
}

h1 {
  margin-bottom: 20px;
  white-space: nowrap;
}

.category {
  align-items: center;
  display: grid;
  grid-template-rows: auto;
  margin-bottom: 25px;
}
</style>
