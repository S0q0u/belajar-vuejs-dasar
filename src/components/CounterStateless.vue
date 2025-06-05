<script setup>
// destructuring props, supaya ga perlu tulis props.name, props.counter
const { name, counter, increment } = defineProps({
  name: String,
  counter: Number,
  increment: Number,
});

defineOptions({
  inheritAttrs: false, // supaya atribut click tidak diteruskan ke elemen div
});
</script>

<template>
  <!-- single element, biar tidak terjadi event propagation (karena semua yang dikirim dari multiplecounter diteruskan ke semua elemen atau fallthrough, jadi event click ada di div juga)-->
  <div>
    <h1>Counter {{ name }}: {{ counter }}</h1>
    <button @click="$emits('click', increment)">Increment {{ name }}</button>
  </div>
</template>
