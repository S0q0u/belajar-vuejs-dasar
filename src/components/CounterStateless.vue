<script setup>
// destructuring props, supaya ga perlu tulis props.name, props.counter
const { name, counter } = defineProps(['name', 'counter']);
</script>

<template>
  <h1>counterer {{ name }}: {{ counter }}</h1>
</template>
