


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

<script setup lang="ts">
  import { ref } from 'vue'

  interface Task {
    text: string
    done: boolean
  }

  const tasks = ref<Task[]>(JSON.parse(localStorage.getItem('tasks') || '[]'))
  const newTask = ref<string>('')

  function addTask(): void {
    if (!newTask.value.trim()) return
    tasks.value.push({ text: newTask.value, done: false })
    newTask.value = ''
    save()
  }

  function removeTask(i: number): void {
    tasks.value.splice(i, 1)
    save()
  }

  function save(): void {
    localStorage.setItem('tasks', JSON.stringify(tasks.value))
  }
</script>

<style scoped>
  .done {
    text-decoration: line-through;
    color: #888;
  }
</style>
