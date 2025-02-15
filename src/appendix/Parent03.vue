<script setup>
import { ref } from 'vue';
import Child02 from './Child03.vue';

let title = ref('title')
</script>
<template>
  <h1>Parent02</h1>
  <p>ref: {{ title }}</p>
  <Child02 
    v-model="title"
  />
</template>