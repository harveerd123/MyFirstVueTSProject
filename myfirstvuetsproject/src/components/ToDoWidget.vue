<script setup lang="ts">

</script>


<template>
  <div>
    <div class="add">
      <input v-model="newTask" @keyup.enter="addTask" placeholder="New task..." />
      <button @click="addTask">Add</button>
    </div>

    <ul class="tasks">
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" v-model="task.done" @change="save" />
        <span :class="{ done: task.done }">{{ task.text }}</span>
        <button @click="removeTask(index)">✖</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
  import { ref, watch } from 'vue'

  const tasks = ref(JSON.parse(localStorage.getItem('tasks') || '[]'))
  const newTask = ref('')

  const addTask = () => {
    if (!newTask.value.trim()) return
    tasks.value.push({ text: newTask.value, done: false })
    newTask.value = ''
    save()
  }

  const removeTask = (i) => {
    tasks.value.splice(i, 1)
    save()
  }

  const save = () => {
    localStorage.setItem('tasks', JSON.stringify(tasks.value))
  }
</script>

<style scoped>
  .add {
    display: flex;
    gap: 10px;
  }

  .tasks {
    list-style: none;
    padding: 0;
    margin-top: 15px;
  }

    .tasks li {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 8px;
    }

  .done {
    text-decoration: line-through;
    color: #888;
  }

  button {
    cursor: pointer;
  }
</style>

