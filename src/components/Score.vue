<script setup>
import { ref } from 'vue';

const score = ref(80);
</script>

<template>
  <h1>Score App</h1>

  <!-- elemen yang pakai v-show tetap ada di dalam DOM, cuma displaynya bisa none -->
  <div v-show="score > 80">Score is {{ score }}</div>

  <!-- elemen yang pakai v- condition bakal dihapus dari DOM kalo ga memenuhi -->
  <div v-if="score > 90">Yayyy cool score {{ score }}!!</div>
  <div v-else-if="score > 70">Good score {{ score }}</div>
  <div v-else>Oops... bad score {{ score }}</div>
</template>

<style scoped></style>
