<script>
import SnakeGame from './components/SnakeGame.vue'

export default {
  name: 'App',
  components: {
    SnakeGame
  }
}
</script>

<template>
  <SnakeGame/>
</template>

<style>
body {
  margin: 0;
}

#app {
  background-color: black;
  height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;
  font-family: 'Roboto Mono', monospace;
}
</style>
