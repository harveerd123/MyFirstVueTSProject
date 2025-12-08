<script setup lang="ts">
  import ToDoWidget from './components/ToDoWidget.vue'
  import NotesWidget from './components/NotesWidget.vue'
  import QuoteWidget from './components/QuoteWidget.vue'
  import WidgetContainer from './components/WidgetContainer.vue'
</script>

<template>
  <div class="dashboard">
    <WidgetContainer title="To-Do List">
      <ToDoWidget />
    </WidgetContainer>

    <WidgetContainer title="Notes">
      <NotesWidget />
    </WidgetContainer>

    <WidgetContainer title="Daily Quote">
      <QuoteWidget />
    </WidgetContainer>
  </div>
</template>

