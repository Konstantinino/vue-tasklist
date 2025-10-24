<script setup>
import { ref } from 'vue'

const number = ref(5)

const increment = () => number.value++
</script>

<template>
  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>

  <button @click="increment">Типо счётчик: {{ number }} код </button>
     <h1> hello</h1>
</template>

<style scoped></style>
