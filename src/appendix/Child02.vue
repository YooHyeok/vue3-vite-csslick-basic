<script setup>
import { defineProps } from 'vue';
  const props = defineProps({
    title: Object
  });
  console.log(props.title.title)
  props.title.title="멍충아" /* 부모 ref 갱신 불가 */
</script>
<template>
  <h2>Child02</h2>
  <input type="text" v-model="props.title.title"> <!-- 부모 ref 갱신 가능 -->
</template>