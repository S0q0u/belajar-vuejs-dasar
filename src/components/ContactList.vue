<script setup>
// define model argumen pertama adalah nama model, argumen kedua adalah object yang berisi type, required, default
const name = defineModel('name', {
  type: String,
});
// menambah modifier
const [email, emailModifiers] = defineModel('email', {
  type: String,
  get: (value) => {
    // kalau ada modifier uppercase maka value di-uppercase
    if (emailModifiers.uppercase) {
      return value.toUpperCase();
    }
    // kalau tidak ada modifier maka value tetap
    else {
      return value;
    }
  },
});
const age = defineModel('age', {
  type: Number,
});
const type = defineModel('type', {
  type: String,
});
const complain = defineModel('complain', {
  type: Boolean,
});
const message = defineModel('message', {
  type: String,
});
</script>

<template>
  <h1>Preview</h1>
  <div>
    <p>Name: {{ name }}</p>
    <p>Email: {{ email }}</p>
    <p>Age: {{ age }}</p>
    <p>Type: {{ type }}</p>
    <p>Complain: {{ complain }}</p>
    <p>Message: {{ message }}</p>
  </div>
</template>
