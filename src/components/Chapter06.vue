<script setup>
import { ref } from 'vue'
const count = ref(0); // 상태변수 추가

</script>
<template>
<button @click="count++">{{ count }}</button> <!-- button태그 추가 및 실행문 바인딩 -->
</template>