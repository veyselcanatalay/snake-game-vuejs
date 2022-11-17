<script setup>
export default {
  name: 'SnakeGame',
}

let board;
let context;
let blockSize = 20;
let cols = 30;
let rows = 20;

let appleAudio;
let gameOverAudio;

let snakeX = 0;
let snakeY = 0;
let tail = [];

let foodX = 0;
let foodY = 0;

let score = 0;

let velocityX = 1;
let velocityY = 0;

let gameOver = false;


window.onload = () => {
  board = document.getElementById('board');
  context = board.getContext('2d');

  appleAudio = new Audio('apple_sound.mp3');
  gameOverAudio = new Audio('game_over_sound.mp3');

  board.width = cols * blockSize;
  board.height = rows * blockSize;

  document.addEventListener('keyup', changeDirection)

  board.addEventListener('click', () => {
    gameOver = false;
    score = 0;
  });

  foodPlace();

  setInterval(update, 1000 / 10);
}

const update = () => {
  //clear screen

  createRect(0, 0, board.width, board.height)

  if (gameOver) {
    //Game end screen

    createText('Game Over', board.width / 2, board.height / 2 - 25, 'center', 50);

    createText(`Score: ${score}`, board.width / 2, board.height / 2 + 25, 'center');

    createText('Click to Start Again', (cols * blockSize) / 2, board.height - 50, 'center');

    return
  }

  // write score

  createText(`Score: ${score}`, 30, 40);

  // Create first food
  createRect(foodX, foodY, blockSize, 'lime');

  // Did it eat
  if (snakeX === foodX && snakeY === foodY) {
    tail.push([foodX, foodY]);

    score += 10;

    appleAudio.play();

    foodPlace()
  }

  // Snake tail
  for (let i = 0; i < tail.length; i++) {
    tail[i] = tail[i - 1];
  }

  if (tail.length) {
    tail[0] = [snakeX, snakeY];
  }

  // Snake position
  snakeX += velocityX * blockSize;
  snakeY += velocityY * blockSize;

  createRect(snakeX, snakeY, blockSize, 'orange');

  for (let i = 0; i < tail.length; i++) {
    createRect(tail[i][0], tail[i][1], blockSize, blockSize, 'lime');
  }

  // Hit the wall
  if (snakeX < 0 || snakeX > cols * blockSize || snakeY < 0 || snakeY > rows * blockSize) {
    gameOverEvent()
  }


  // You're here

  // https://www.youtube.com/watch?v=wNTh_8CGj6s&ab_channel=Codeminton 16:07 min

}
const foodPlace = () => {
}
const changeDirection = () => {
}

const gameOverEvent = () => {
}

const createRect = () => {
}

const createText = () => {
}

</script>

<template>
  <div class="container">
    <h1>Snake Game</h1>

    <canvas id="board"></canvas>
  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  background-color: black;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;

  h1 {
    color: lime;
    margin-bottom: 2.5rem;
  }

  canvas {
    border: 3px solid lime;
  }
}
</style>
