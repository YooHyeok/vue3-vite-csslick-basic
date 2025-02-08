<script setup>
import { ref } from 'vue' // 상태변수를 선언하는 함수

const msg = ref('Chapter1') // ref함수를 통해 변수 선언 - 데이터의 변경을 감시하고 컴포넌트를 자동으로 업데이트 하는 `반응형 변수`
</script>
<template>
  <h1>{{ msg }}</h1> <!-- 데이터 바인딩: 반응형 변수 삽입 - vue에서 `mustache`라고 부름 -->
  <input v-model="msg"> <!-- v-디렉티브: 지시자 라고도 부른다. v-model의 경우 변수 값을 입력할 수 있는 문법이다.  -->
</template>