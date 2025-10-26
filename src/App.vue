<script setup>
import { ref, reactive } from 'vue'

const posts = ref([])
const post = reactive({
  title: '',
  body: ''
})

const getTask = function() {
  posts.value.unshift({
    title: post.title,
    body: post.body
  })
}
</script>

<template>
  <div class="main">
    <section class="tasklist">
      <div class="tasklist-form">
        <input v-model="post.title" name="task-title" type="text" class="task-title" placeholder="Название задачи">
        <textarea v-model="post.body" name="task-body" class="task-body" placeholder="Описание задачи"></textarea>
        <button @click="getTask" class="task-btn">Создать задачу</button>
      </div>
      {{ posts }}  
    </section>

  </div>
</template>

<style>
body {
  background-color: #00000024;
  margin: 0;
  padding: 0;
}
.main {
  /* min-width: 100%; */
  height: 100vh;
  background-color: #00000024;
}
.tasklist {
  margin: 0 auto;
  width: 50%;
  border: 1px solid #00000021;
  border-radius: 10px;
  background-color: white;
}
.tasklist-form {
  display: flex;
  flex-direction: column;
  padding: 30px 15px 15px;
}
input, textarea {
  padding: 5px;
  border: none;
  border-bottom: 1px solid #00000021;
  margin-bottom: 15px;
  outline: none;
}
button {
  width: 130px;
  padding: 10px;
  background-color: rgb(67, 162, 127);
  color: white;
  border: none;
  border-radius: 10px;
  outline: none;
  cursor: pointer;
  transition: all .3s;
}
button:hover {
  transform: translateY(-3px);
}
</style>
