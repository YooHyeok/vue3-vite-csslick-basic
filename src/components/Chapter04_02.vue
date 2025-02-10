<script setup>
import { ref } from 'vue';

const isOpen = ref(true);
const closeModal = () => {
  isOpen.value = false
}

</script>
<template>
  <h1>조건부 랜더링(Conditional Redering)</h1>
  <div class="modal" v-if="isOpen">
    <h2>Notice</h2>
    <p>50% off today</p>
    <button @click="isOpen=false">close</button>
    <button @click="closeModal">close</button>
  </div>
</template>
<style scoped>
.modal {
  background-color: #ccc;
  padding: 1rem;
  h2 { margin: 0; color: red; }
}
</style>