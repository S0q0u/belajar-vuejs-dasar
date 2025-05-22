<script setup>
// import semua komponen yang ada di dalam folder src/components
import { ref } from 'vue';
import blog from './Blog.vue';
import contact from './Contact.vue';
import about from './About.vue';

// currentPage adalah variable yang berisi nama komponen yang akan ditampilkan
// defaultnya adalah about
const currentPage = ref('about');

// buat variable pages yang berisi semua komponen
const pages = {
  about: about,
  blog,
  contact,
};
</script>

<template>
  <button @click="currentPage = 'about'">About</button>
  <button @click="currentPage = 'blog'">Blog</button>
  <button @click="currentPage = 'contact'">Contact</button>
  <!-- component dibinding sama is karena mau ambil variabel, komponen apa yang mau ditampilkan -->
  <component :is="pages[currentPage]" />
</template>
