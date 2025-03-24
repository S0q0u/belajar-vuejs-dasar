<script setup>
import { reactive } from 'vue';
import ContactForm from './ContactForm.vue';
import ContactList from './ContactList.vue';

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
  <ContactForm v-model="contact" />

  <!-- sebutin argumennya, !! sebenarnya ini contoh tidak ideal karena bisa dijadiin satu model dan pindahin ke props aja !!-->
  <!-- menambah modifier uppercase di email -->
  <ContactList
    v-model:name="contact.name"
    v-model:email.uppercase="contact.email"
    v-model:age="contact.age"
    v-model:type="contact.type"
    v-model:complain="contact.complain"
    v-model:message="contact.message"
  />
</template>

<style scoped></style>
