<script setup>
import { ref } from 'vue'
const count = ref(0);
const inputValue = ref(''); // 상태변수 추가
const handleInput = (e) => { // 이벤트 바인딩 함수 추가
  inputValue.value = e.target.value
}
</script>
<template>
<button @click="count++">{{ count }}</button>
<br>
<p>{{ inputValue }}</p>
<input type="text" @input="handleInput" /> <!-- input 태그 추가 및 함수 바인딩 -->
</template>