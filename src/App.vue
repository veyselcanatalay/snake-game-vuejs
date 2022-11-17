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
  <img alt="Vue logo" src="./assets/logo.png">
  <SnakeGame msg="Welcome to Your Vue.js App"/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
