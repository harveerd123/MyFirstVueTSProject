

<template>
  <div>
    <p class="quote">"{{ quote }}"</p>
    <button @click="newQuote">New Quote</button>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue'

  const quotes: string[] = [
    "Success is not final; failure is not fatal.",
    "Do something today that your future self will thank you for.",
    "The only limit is your mind.",
    "Small steps every day."
  ]

  const quote = ref<string>(
    localStorage.getItem('dailyQuote') || random()
  )

  function random(): string {
    return quotes[Math.floor(Math.random() * quotes.length)]
  }

  function newQuote(): void {
    quote.value = random()
    localStorage.setItem('dailyQuote', quote.value)
  }
</script>

<style scoped>
  .quote {
    font-style: italic;
    margin-bottom: 15px;
  }
</style>
