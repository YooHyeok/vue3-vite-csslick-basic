<script setup>
  import { ref } from 'vue';
  let count = 0;
  const refCount = ref(0);
  const increment = () => {
    count++;
    refCount.value++;
    alert(count)
  }
</script>
<template>
  <p>count: {{ count }}</p>
  <!-- <p>refCount: {{ refCount }}</p> --> <!-- 주석시 cnt 반응하지 않음 주석해제시 cnt 함께 반응 -->
  <button @click="increment">Count++</button>
</template>