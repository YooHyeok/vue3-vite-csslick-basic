<script setup>
  let count = 0;
  const increment = () => {
    count++;
    alert(count)
  }
</script>
<template>
  <p>count: {{ count }}</p>
  <button @click="increment">Count++</button>
</template>