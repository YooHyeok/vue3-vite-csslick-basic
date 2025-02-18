<script setup>
  import { ref } from 'vue';
  import Child02 from './Child02.vue';

  let title = ref({title: 'title'})
</script>
<template>
  <h1>Parent02</h1>
  <p>ref: {{ title.title }}</p>
  <Child02 :title="title"/>
</template>