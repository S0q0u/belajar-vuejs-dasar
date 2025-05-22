<script setup>
import { ref, useSlots } from 'vue';
// const { title } = defineProps({
//   title: String,
// });

const slots = useSlots();
const counter = ref(0);
</script>

<template>
  <!-- <h1>{{ title }}</h1> -->
  <!-- cek apakah ada slot header, jika ada maka tampilkan -->
  <div v-if="slots.header">
    <!-- atributnya counter -->
    <slot name="header" :counter="counter">
      <h1>Default header</h1>
    </slot>
  </div>
  <div v-if="slots.default">
    <!-- fallthrough content, muncul sebagai default kalau slotnya tidak berisi content -->
    <slot name="default" :counter="counter">
      <p>Belum ada isi konten</p>
    </slot>
  </div>
  <div v-if="slots.footer">
    <slot name="footer" :counter="counter">
      <p>Default footer</p>
    </slot>
  </div>
  <div>
    <button @click="counter++">Increment Counter</button>
  </div>
</template>
