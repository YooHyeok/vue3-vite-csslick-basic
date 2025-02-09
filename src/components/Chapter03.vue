<!-- Chapter2. 데이터 바인딩 -->
<script setup>
/**
 * 데이터를 화면에 출력하는 것을 데이터 바인딩이라 하며, 데이터가 변경되었을 때 화면에 업데이트 되어야 한다. 
 * 이런것들을 리액티브한 value값들 이라고 한다.
 * Vue에서는 정적인 변수값과 리액티브한 변수값이 있을 수 있다.
 * 
 * v-bind 디렉티브를 통한 데이터 바인딩으로 속성값이나, 텍스트노드 값들을 표시할 수 있다.
 */
  import { ref } from 'vue';
  const myStyle = { color: 'red' }
  const title = "Chapter2"
</script>
<template>
  <h1 v-bind:style="myStyle">{{ title }}</h1>
</template>