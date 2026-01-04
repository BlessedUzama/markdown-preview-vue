<template>
  <div
    class="preview"
    v-html="compiledMarkdown"
  ></div>
</template>

<script setup>
import { computed, watch, nextTick } from "vue"
import { marked } from "marked"
import hljs from "highlight.js"
import "highlight.js/styles/github.css"

marked.setOptions({
  langPrefix: "language-"
})

const props = defineProps({
  markdown: String
})

const compiledMarkdown = computed(() =>
  marked.parse(props.markdown)
)

watch(compiledMarkdown, async () => {
  await nextTick()

  document
    .querySelectorAll("pre code")
    .forEach((block) => {
      hljs.highlightElement(block)
    })
})
</script>

<style scoped>
.preview {
  padding: 1rem;
  border: 1px solid #ddd;
  min-height: 300px;
  overflow: auto;
}

.preview pre {
  background: #f6f8fa;
  padding: 1rem;
  border-radius: 6px;
  overflow-x: auto;
}
</style>
