<script setup>
import Modal from './Modal.vue';
import { ref } from 'vue';

const isModal = ref(true)
</script>
<template>
  <div>
    <Modal v-if="isModal"/>
    <button @click="isModal=!isModal">toggle</button>
  </div>
</template>
<style scoped>
  .modal {
    background: #ccc;
    padding: 1rem;
  }
</style>
