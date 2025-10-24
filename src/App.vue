<script setup>
import { ref } from 'vue'

const number = ref(5)

const increment = () => number.value++
</script>

<template>
  <h1>Increment Counter. You Know</h1>

  <button @click="increment">Типо chicken: {{ number }}</button><br/>
  <button @click="number=0">Clear counter</button>
</template>

<style scoped></style>
