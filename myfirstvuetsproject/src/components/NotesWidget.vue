<script setup lang="ts">

</script>

<template>
<div>
  <textarea v-model="notes" @input="save" placeholder="Write notes here..."></textarea>
</div>
</template>

<script setup>
  import { ref } from 'vue'

  const notes = ref(localStorage.getItem('notes') || '')

  const save = () => {
    localStorage.setItem('notes', notes.value);
  }
</script>

<style scoped>
  textarea {
    width: 100%;
    height: 200px;
    padding: 10px;
    border-radius: 6px;
    border: 1px solid #ccc;
    resize: vertical;
  }
</style>
