<template>
  <div class="container">
    <div v-if="showDialog === 'price'" class="btnContainer">
      <button class="btn" @click="handleBtnClick">${{ props.question.price }}</button>
    </div>
    <div class="btnContainer" v-if="showDialog === 'question'" @click="handleQuestionClick">
      <button>
        <p>{{ props.question.qa.question }}</p>
        <p v-if="props.question.multipleChoice" class="multipleChoiceP">Multiple Choice</p>
      </button>
    </div>
    <div
      class="btnContainer"
      v-if="showDialog === 'multipleChoice'"
      @click="handleMultipleChoiceClick"
    >
      <button>
        <p>A: {{ props.question.qa.a }}</p>
        <p>B: {{ props.question.qa.b }}</p>
        <p>C: {{ props.question.qa.c }}</p>
        <p>D: {{ props.question.qa.d }}</p>
      </button>
    </div>
    <div class="btnContainer" v-if="showDialog === 'answer'" @click="handleAnswerClick">
      <button>
        <p>{{ props.question.qa.answer }}</p>
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps(['question'])
const showDialog = ref('price')

const handleBtnClick = () => {
  showDialog.value = 'question'
}

const handleQuestionClick = () => {
  if (props.question.multipleChoice) {
    showDialog.value = 'multipleChoice'
    return
  }
  showDialog.value = 'answer'
}

const handleMultipleChoiceClick = () => {
  showDialog.value = 'answer'
}

const handleAnswerClick = () => {
  showDialog.value = ''
}
</script>

<style scoped>
.container {
  cursor: pointer;
  height: 150px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5px;
  background-color: #060ce9;
  color: #ebbe00;
  border: 1px solid black;
}

.btnContainer {
  height: 100%;
  width: 100%;
}

.multipleChoiceP {
  font-size: 12px;
  margin-top: 10px;
  color: greenyellow;
}

p {
  font-size: 20px;
}

button {
  height: 100%;
  width: 100%;
  font-size: 32px;
  color: #ebbe00;
  background-color: #060ce9;
  border: none;
  cursor: pointer;
  text-align: center;
  max-width: 225px;
}

h2 {
  font-size: 18px;
}
</style>
