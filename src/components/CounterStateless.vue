<script setup>
// destructuring props, supaya ga perlu tulis props.name, props.counter
const { name, counter, increment } = defineProps({
  name: String,
  counter: Number,
  increment: Number,
});

// define emits untuk mengirim event
const emits = defineEmits(['click']);
</script>

<template>
  <div>
    <h1>Counter {{ name }}: {{ counter }}</h1>
    <!-- increment itu event parameter yang dikirim -->
    <button @click="emits('click', increment)">Increment {{ name }}</button>
  </div>
</template>
