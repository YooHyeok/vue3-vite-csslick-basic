<script setup>
import { ref } from 'vue';
import Child01 from './Child01.vue';

let title = ref('title')
</script>
<template>
  <h1>Parent</h1>
  <p>ref: {{ title }}</p>
  <Child01 
    :title="title"
    @onInput="(value) => { title = value }"
  />
</template>