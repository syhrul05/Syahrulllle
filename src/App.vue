<template>
  <div class="container">
    <header>
      <h1 :class="{ 'title-large': isLarge }">Selamat Datang!</h1>
    </header>
    <main>
      <p :style="{ color: textColor }">Ini adalah halaman web sederhana dengan beberapa elemen HTML.</p>
      <input type="text" v-model="inputText" @input="updateText" placeholder="Ketik sesuatu...">
      <p v-if="inputText !== ''" class="typed-text">Anda mengetik: {{ inputText }}</p>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isLarge = ref(false);
const textColor = ref('black');
const inputText = ref('');

const updateText = () => {
  if (inputText.value.length > 10) {
    isLarge.value = true;
    textColor.value = 'blue';
  } else {
    isLarge.value = false;
    textColor.value = 'black';
  }
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

header {
  text-align: center;
  margin-bottom: 20px;
}

main {
  text-align: center;
}

input[type="text"] {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 20px;
}

p {
  font-size: 18px;
  line-height: 1.6;
}

.typed-text {
  font-weight: bold;
  color: green;
}
</style>
