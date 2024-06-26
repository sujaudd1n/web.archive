<script setup>
import { ref } from 'vue';

const charSet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()+=-[]\\|}{;\"\'<>?/}';
const texts = ref('hello');

function generateText() {
  const screenWidth = window.innerWidth;
  const screenHeight = window.innerHeight;
  const charCount = screenHeight * screenWidth;
  let text = '';
  for (let i = 0; i < charCount; ++i) {
    text += charSet[Math.floor(Math.random() * charSet.length)]
  }
  return text;
}

texts.value = generateText();
</script>

<template>
  <div class="texts"> {{ texts }}</div>
</template>

<style scoped>
@keyframes tremble {
  0% {
    text-shadow: 3px 0px 1px #ccc;
  }
  25% {
    text-shadow: -3px 0 1px #ccc;
  }
  50% {
    text-shadow: 0 -3px 1px #ccc;
  }
  75% {
    text-shadow: 3px 3px 1px #ccc;
  }
  100% {
    text-shadow: 3px 0px 1px #ccc;
  }

}

.texts {
  color: green;
  font-size: 20px;
  animation: tremble 800ms linear 0s infinite;
  word-break: break-all;
  font-family: monospace;
  position: absolute;
  top: -10px;
  left: -10px;
  right: -70px;
  bottom: -10px;
}
</style>
