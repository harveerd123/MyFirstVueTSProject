

<template>
  <div>
    <textarea v-model="notes" @input="save" placeholder="Write notes here..."></textarea>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue'

  const notes = ref<string>(localStorage.getItem('notes') || '')

  function save(): void {
    localStorage.setItem('notes', notes.value)
  }
</script>
