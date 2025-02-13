<script setup>
import { onMounted, onUnmounted } from 'vue';
onMounted(() => {
  console.log("Mounted")
})
onUnmounted(() => {
  console.log("Unmounted")
})

console.log("setup")
</script>
<template>
  <div class="modal">
    <h2>Modal</h2>
    <p>모달입니다.</p>
  </div>
</template>