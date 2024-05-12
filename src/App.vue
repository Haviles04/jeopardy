<template>
  <div class="container">
    <h1>Mothers Day Jeopardy</h1>
    <Board />
  </div>
</template>

<script setup>
import Board from '@/components/Board.vue'
</script>

<style scoped>
* {
  text-align: center;
}

h1 {
  margin: 25px;
}

.container {
  display: flex;
  height: 100%;
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #979797;
}
</style>
