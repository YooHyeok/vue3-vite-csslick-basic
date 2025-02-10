<script setup>
  const foods = ['apple', 'banana', 'mango']
  const foodObjs = [
    { id: 1, name: 'apple' },
    { id: 2, name: 'banana' },
    { id: 3, name: 'mango' }
  ]
</script>
<template>
  <h1>반복문</h1>
  <ul>
    <li>{{ foods[0] }}</li>
    <li>{{ foods[1] }}</li>
    <li>{{ foods[2] }}</li>
  </ul>
  <ul>
    <li v-for="(food, index) in foods" :key="index">{{ index }}: {{ food }} </li>
  </ul>
  <ul>
    <li v-for="(food) in foodObjs" :key="food.id">{{ food.id }}: {{ food.name }} </li>
  </ul>
</template>