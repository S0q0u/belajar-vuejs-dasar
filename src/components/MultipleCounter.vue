<script setup>
import Counter from './Counter.vue';
import CounterStateless from './CounterStateless.vue';
import { ref } from 'vue';

const counter1 = 'Lin';
const counter = ref(0);
</script>

<template>
  <Counter :name="counter1" initial-count="10" />
  <Counter name="Na" initial-count="100" />

  <CounterStateless name="Wawan" :counter="counter" />
  <CounterStateless name="Xiao" :counter="counter" />
  <button @click="counter++">Increment Counter</button>
</template>

<style scoped></style>
