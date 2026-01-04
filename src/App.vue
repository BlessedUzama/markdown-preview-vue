<template>
  <h1>Markdown Preview</h1>

  <div class="container">
    <textarea v-model="markdown" />
    <Preview :markdown="markdown" />
  </div>
</template>

<script setup>
import { ref } from "vue"
import Preview from "./components/Preview.vue"

const markdown = ref(`\`\`\`js
const sum = (a, b) => a + b
console.log("Hello World")
\`\`\``)
</script>

<style>
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

textarea {
  min-height: 300px;
}
</style>
