<template>
  <div class="main">
    <h1 class="main__title">Tic-Tac-Toe</h1>
    <Board />
  </div>
</template>

<script setup lang="ts">
import Board from './components/Board.vue'
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Cabin&display=swap');

:root {
  --bg-1: #333;
  --bg-2: #444;
  --bg-3: #555;
  
  font-family: 'Cabin', sans-serif;
  background-color: var(--bg-1);
  height: 100vh;
  display: flex;
  justify-content: center;
  text-align: center;
  color: white;
}

.main__title {
  font-size: 48px;
}
</style>