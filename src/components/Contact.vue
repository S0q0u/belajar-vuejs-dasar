<script setup>
import { reactive } from 'vue';

const contact = reactive({
  name: '',
  email: '',
  age: 0,
  type: 'Regular',
  complain: false,
  message: '',
});
</script>

<template>
  <h1>Contact Us</h1>
  <form action="">
    <div>
      <label for="name">Name: </label>
      <input type="text" name="name" id="name" v-model="contact.name" />
    </div>
    <div>
      <label for="email">Email: </label>
      <input type="email" name="email" id="email" v-model="contact.email" />
    </div>
    <div>
      <label for="age">Age: </label>
      <input type="number" name="age" id="age" v-model.number="contact.age" />
    </div>
    <div>
      <label for="type">Type: </label>
      <select name="type" id="type" v-model="contact.type">
        <option value="Regular">Regular</option>
        <option value="VIP">VIP</option>
      </select>
    </div>
    <div>
      <label for="complain">Complain: </label>
      <input
        type="checkbox"
        name="complain"
        id="complain"
        v-model="contact.complain"
      />
    </div>
    <div>
      <label for="message">Message: </label>
      <textarea
        name="message"
        id="message"
        v-model="contact.message"
      ></textarea>
    </div>
  </form>

  <h1>Preview</h1>
  <div>
    <p>Name: {{ contact.name }}</p>
    <p>Email: {{ contact.email }}</p>
    <p>Age: {{ contact.age }}</p>
    <p>Type: {{ contact.type }}</p>
    <p>Complain: {{ contact.complain }}</p>
    <p>Message: {{ contact.message }}</p>
  </div>
</template>

<style scoped></style>
