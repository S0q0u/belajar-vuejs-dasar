<script setup>
console.info('Helloooo');

const hello = '<h1>Hello Vue</h1>';
// const classHello = 'hello';
// const id = 'hello';
const buttonDisabled = true;

//multiple attribute, wrap di satu object
const data = {
  id: 'hello',
  class: 'hello',
};

function helloFunction() {
  return 'ini hello function';
}
</script>

<template>
  <!-- <h1 class="hello">{{ hello }}</h1> -->
  <!-- <h1 :id v-bind:class="classHello">{{ hello }}</h1> -->
  <h1 v-bind="data">{{ hello.toUpperCase() }}</h1>

  <h2>{{ 100 * 200 }}</h2>
  <h2>{{ helloFunction() }}</h2>

  <!-- <div :class="classHello" v-html="hello"></div> -->
  <div :class="data.class" v-html="hello"></div>

  <!-- <button disabled>This is Button</button> -->
  <button :disabled="buttonDisabled">This is Button</button>
</template>

<style scoped>
.hello {
  color: red;
}
#hello {
  text-align: center;
}
</style>
