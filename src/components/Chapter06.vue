<script setup>
import { ref } from 'vue'
const count = ref(0);
const inputValue = ref('');
const handleInput = (e) => {
  inputValue.value = e.target.value
}
const modelValue = ref(''); // 상태변수 추가
</script>
<template>
<button @click="count++">{{ count }}</button>
<br>
<p>inputValue: {{ inputValue }}</p>
<input type="text" @input="handleInput" />
<br>
<p>modelValue: {{ modelValue }}</p>
<input type="text" v-model="modelValue" /> <!-- input 태그 추가 및 v-model 상태변수 바인딩 -->
</template>