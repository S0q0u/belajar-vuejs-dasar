<script setup>
import Counter from './Counter.vue';
import CounterStateless from './CounterStateless.vue';
import { ref } from 'vue';

const counter1 = 'Lin';
const counter = ref(0);

function increment(value) {
  counter.value += value;
}
</script>

<template>
  <Counter :name="counter1" initial-count="10" />
  <Counter name="Na" initial-count="100" />

  <!-- @click nama event yang di emit -->
  <!-- <CounterStateless
    name="Wawan"
    :counter="counter"
    v-on:click="() => (counter += 1)"
  />
  <CounterStateless
    name="Xiao"
    :counter="counter"
    @click="() => (counter += 2)"
  /> -->

  <CounterStateless
    name="Wawan"
    :counter="counter"
    :increment="1"
    v-on:click="increment"
  />
  <CounterStateless
    name="Xiao"
    :counter="counter"
    :increment="2"
    @click="increment"
  />
</template>

<style scoped></style>
