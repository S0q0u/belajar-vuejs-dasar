<script setup>
import { nextTick, ref } from 'vue';

// let count = 0;

console.info('Load Component');
let counter = ref({
  count: 0,
  name: 'Lin',
});

// function Increment() {
//   // string concatenation --> nanti count yang awalnya angka berubah jadi string. kurang rapi kalo variabel yang disisipkan banyak
//   //   console.info('increment counter: ' + count);
//   // template literal. lebih rapi karena memungkinkan ekspresi langsung di dalam string (misalnya: ${count + 1})
//   //   console.info(`increment counter: ${count}`);
//   //   count++;
//   //   document.getElementById('count').innerText = `Counter: ${count}`;

//   // pakai reactive state
//   console.info(`increment counter: ${counter.value.count}`);
//   //   counter.value ={
//   //     name: counter.value.name,
//   //     count: counter.value.count + 1
//   //   }

//   counter.value.count++;
// }

async function Increment() {
  console.info(`increment counter: ${counter.value.count}`);
  counter.value = {
    name: counter.value.name,
    count: counter.value.count + 1,
  };

  await nextTick();
  console.log('Increment count after nextTick');
}
</script>

<template>
  <div>
    <!-- <h1 id="count">Counter: {{ count }}</h1> -->
    <h1 id="count">Counter {{ counter.name }}: {{ counter.count }}</h1>
    <button v-on:click="Increment()">Increment</button>
  </div>
</template>
