<script setup>
import { onWatcherCleanup, ref, watch, watchEffect } from 'vue';
import ProductDetail from './ProductDetail.vue';

// state
// const productId = ref('');
const productId = ref('product1');
const product = ref(null);

// kalau state productId berubah, jalanin functionnya
// watch(productId, async (newVal, oldVal) => {
//   if (newVal) {
//     // ambil data json product pakai AJAX
//     const response = await fetch(`/${newVal}.json`);
//     // simpan ke state product
//     product.value = await response.json();
//   } else {
//     product.value = null;
//   }
// });

// menambah watch option immediate true(supaya langsung trigger callback functionnya dari awal diload)
// watch(
//   productId,
//   async (newVal, oldVal) => {
//     const response = await fetch(`/${newVal}.json`);
//     product.value = await response.json();
//   },
//   {
//     immediate: true,
//   }
// );

// pakai watchEffect(callback function), jadi gaperlu nyebut state apa dan immediate true
watchEffect(async () => {
  // karena onWatcherCleanup ga mendukung async, jadi harus ditambahkan sebelum manggil await
  onWatcherCleanup(() => {
    console.log('Clean Up');
  });

  console.log('call watch callback');
  const response = await fetch(`/${productId.value}.json`);
  product.value = await response.json();
});
</script>

<template>
  <!-- pilih product ID -->
  <label for="productId">
    Product Id:
    <select v-model="productId">
      <!-- <option value=""></option> -->
      <option value="product1">Product 1</option>
      <option value="product2">Product 2</option>
      <option value="product3">Product 3</option>
    </select>
  </label>

  <!-- kalau milih product, tampilin datanya -->
  <div v-if="product">
    <!-- <h1>Product</h1>
    <p>Id: {{ product.id }}</p>
    <p>Name: {{ product.name }}</p>
    <p>Price: {{ product.price }}</p> -->
    <ProductDetail
      :id="product.id"
      :name="product.name"
      :price="product.price"
    />
  </div>
</template>

<style scoped></style>
