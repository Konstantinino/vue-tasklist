<script setup>
import { ref, reactive } from 'vue'

const tasks = ref([])
const task = reactive({
  title: '',
  body: ''
})

const addTask = function() {
  tasks.value.unshift({
    title: task.title,
    body: task.body
  })

  Object.assign(task, {
    title: '',
    body: ''
  })
}

const deleteTask = function(task) {
  tasks.value = tasks.value.filter((item => item != task))
}
</script>

<template>
  <div class="task-manager">
    <div class="task-form">
      <input v-model="task.title" type="text" class="task-title" placeholder="Заголовок">
      <textarea v-model="task.body" name="task-body" id="" class="task-body" placeholder="Содержание"></textarea>
      <button @click="addTask" class="task-btn">Создать</button>
    </div>
    <ul v-if="tasks.length>0" class="task-list">
      <li v-for="task in tasks" class="task-item" :key="task">
        <div class="task-content">
          <h2 class="task-item-title">{{ task.title }}</h2>
          <p class="task-item-body">{{ task.body }}</p>
        </div>
        <div class="task-controlers">
          <div class="task-edit">
            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="100" height="100" viewBox="0 0 24 24">
              <path d="M10.107 6.292l-6.704 9.766c-.128.187-.203.404-.217.631l-.183 2.984c-.027.438.178.858.54 1.106C3.754 20.926 4.001 21 4.25 21c.177 0 .354-.037.52-.113l2.719-1.243C7.695 19.55 7.872 19.401 8 19.214l6.704-9.765L10.107 6.292zM16.118 7.388l1.147-1.671c.213-.311.275-.701.167-1.062-.037-.123-.388-1.226-1.468-1.968S13.729 2.012 13.6 2.022c-.375.03-.718.228-.932.539l-1.147 1.67L16.118 7.388zM19.25 18.5A1.25 1.25 0 1019.25 21 1.25 1.25 0 1019.25 18.5zM15.25 18.5A1.25 1.25 0 1015.25 21 1.25 1.25 0 1015.25 18.5zM11.25 18.5A1.25 1.25 0 1011.25 21 1.25 1.25 0 1011.25 18.5z"></path>
            </svg>
          </div>
          <div @click="deleteTask(task)" class="task-delete">
            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="100" height="100" viewBox="0 0 24 24">
              <path d="M 10.806641 2 C 10.289641 2 9.7956875 2.2043125 9.4296875 2.5703125 L 9 3 L 4 3 A 1.0001 1.0001 0 1 0 4 5 L 20 5 A 1.0001 1.0001 0 1 0 20 3 L 15 3 L 14.570312 2.5703125 C 14.205312 2.2043125 13.710359 2 13.193359 2 L 10.806641 2 z M 4.3652344 7 L 5.8925781 20.263672 C 6.0245781 21.253672 6.877 22 7.875 22 L 16.123047 22 C 17.121047 22 17.974422 21.254859 18.107422 20.255859 L 19.634766 7 L 4.3652344 7 z"></path>
            </svg>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}
ul {
  list-style-type: none;
}
.task-manager {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
.task-form {
  display: flex;
  flex-direction: column;
  padding: 20px 50px;
  width: 50%;
  border: 1px solid #f0f0f0;
  border-radius: 5px;
  margin-bottom: 10px;
}
.task-title, .task-body {
  padding: 5px;
  border: none;
  border-bottom: 1px solid #cccccc;
  font-size: 15px;
  margin-bottom: 15px;
}
.task-btn {
  width: 100px;
  background-color: #239718;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px;
  cursor: pointer;
}
.task-list {
  display: flex;
  flex-direction: column;
  align-items: start;
  width: 50%;
  border-radius: 5px;
  padding: 0;
  margin: 0;
}
.task-item {
  width: 100%;
  border: 1px solid #f0f0f0;
  padding: 10px 30px;
  margin-bottom: 10px;
  display: flex;
}
.task-content {
  width: 90%;
}
.task-controlers {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
}
.task-edit, .task-delete {
  cursor: pointer;
}
.task-edit>svg, .task-delete>svg {
  width: 20px;
  height: auto;
}
</style>
