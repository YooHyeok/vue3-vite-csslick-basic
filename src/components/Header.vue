<script setup>
  import { defineProps } from 'vue'
  const props = defineProps({
    title: String
  })
</script>
<template>
  <header>
    <h1>{{ props.title }}</h1>
  </header>
</template>