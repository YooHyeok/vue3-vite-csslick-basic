<script setup>
import { ref } from 'vue';
import Child03 from './Child03.vue';

let title = ref('title')
</script>
<template>
  <h1>Parent03</h1>
  <p>ref: {{ title }}</p>
  <Child03
    v-model="title"
  />
</template>