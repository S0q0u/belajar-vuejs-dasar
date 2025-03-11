<script setup>
import { computed, reactive, ref } from 'vue';

let person = reactive({
  firstname: '',
  lastname: '',
});

function sayHello() {
  person.firstname = document.getElementById('firstname').value;
  person.lastname = document.getElementById('lastname').value;
  // alert(`Hello ${person.firstname + ' ' + person.lastname}`);
}

// function fullname() {
//   console.log('fullname called!');
//   return `${person.firstname + ' ' + person.lastname}`;
// }

// computed dipakai buat ngebaca perubahan state
const fullname = computed((oldName) => {
  console.log(`change old name ${oldName}`);
  return `${person.firstname + ' ' + person.lastname}`;
});

const counter = ref(0);

function increment() {
  console.log('increment called!');
  counter.value++;
}

// event argument
function changeFirstName(event) {
  // person.firstname = document.getElementById('firstname').value;
  person.firstname = event.target.value;
}

function changeLastName(event) {
  // person.lastname = document. getElementById('lastname').value;
  person.lastname = event.target.value;
}
</script>

<template>
  <div>
    <form action="">
      <!-- <button v-on:click="increment">Increment {{ counter }}</button> <br /> -->
      <!-- dibanding manggil function, kita bisa jadiin inline statement kalo functionnya sederhana -->
      <!-- untuk pakai didalam template, gaperlu panggil atribut valuenya (counter.value) -->
      <button v-on:click="counter++">Increment {{ counter }}</button> <br />
      <input
        type="text"
        id="firstname"
        placeholder="First Name"
        v-on:input="changeFirstName"
      />
      <input
        type="text"
        id="lastname"
        placeholder="Last Name"
        @input="changeLastName"
      />
      <!-- event modifier ditaruh setelah argumen. -->
      <button v-on:click.prevent="sayHello">Say Hello</button>
    </form>
  </div>

  <!-- <h1>Hello {{ person.firstname }} {{ person.lastname }}</h1> -->
  <h1>Hello {{ fullname }}</h1>
</template>
