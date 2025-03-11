<script setup>
const items = [
  {
    id: 1,
    text: 'Belajar Vue 3',
    done: true,
  },
  {
    id: 2,
    text: 'Belajar Vue Router',
    done: false,
  },
  {
    id: 3,
    text: 'Belajar Pinia',
    done: false,
  },
  {
    id: 4,
    text: 'Belajar Pinia 2',
    done: false,
  },
];
</script>

<template>
  <h1>Todo List</h1>
  <!-- list for array -->
  <!-- <ul>
    <li v-for="item in items">{{ item.text }}</li>
  </ul> -->

  <!-- list for object -->
  <!-- <ul v-for="item in items" :key="item.id">
    <li v-for="(value, key) in item">{{ key }}: {{ value }}</li>
  </ul> -->

  <!-- v-if dan v-for pada satu element yang sama, yang dibaca adalah if dulu. jadi ini contoh salah (error) -->
  <!-- <ul v-for="item in items" :key="item.id" v-if="!item.done">
    <li v-for="(value, key) in item">{{ key }}: {{ value }}</li>
  </ul> -->

  <!-- cara benar: v-for dinaikkan ke atas, karena gamau bikin tag apapun bisa pake tag template (gabakal dijadiin element di DOM) -->
  <template v-for="item in items">
    <ul :key="item.id" v-if="!item.done">
      <li v-for="(value, key) in item">{{ key }}: {{ value }}</li>
    </ul>
  </template>

  <!-- list for range -->
  <h1 v-for="i in 10">Hello ke-{{ i }}</h1>
</template>
