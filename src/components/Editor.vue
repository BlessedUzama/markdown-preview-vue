<script setup>
defineProps({ modelValue: String })
defineEmits(["update:modelValue"])
</script>

<template>
  <textarea
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    style="height:300px;width:100%"
  />
</template>
