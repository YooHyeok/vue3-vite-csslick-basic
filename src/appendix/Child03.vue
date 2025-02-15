<script setup>
import {  defineModel } from 'vue';
  const model = defineModel();
  console.log(model.value)
  model.value="메롱"
</script>
<template>
  <h2>Child02</h2>
  <p>model: {{ model }}</p>
  <input 
    type="text" 
    v-model="model"
  >
</template>