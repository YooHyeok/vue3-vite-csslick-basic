<script setup>
import { defineProps, defineEmits } from 'vue';
  const props = defineProps({
    title: String
  });
  const emits = defineEmits(['onInput']);
</script>
<template>
  <h2>Child01</h2>
  <p>props: {{ props.title }}</p>
  <input 
    type="text" 
    :value="props.title" 
    @input=" 
      inputText = $event.target.value;
      emits('onInput', inputText)
    "
  >
</template>