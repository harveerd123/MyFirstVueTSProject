<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>

<template>
  <div class="widget">
    <h2>{{title}}</h2>
    <div><slot /></div>
  </div>
</template>

<style scoped>
.widget{
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0,0,0,.1);
}
</style>
