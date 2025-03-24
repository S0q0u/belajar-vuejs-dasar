<script setup>
const model = defineModel({
  type: Object,
  required: true,
  default: {
    name: '',
    email: '',
    age: 0,
    type: 'Regular',
    complain: false,
    message: '',
  },
  //   misal ingin buat namanya uppercase setiap di get
  get: (value) => {
    value.name = value.name.toUpperCase();
    return value;
  },
});
</script>

<template>
  <form>
    <div>
      <label for="name">Name: </label>
      <input type="text" name="name" id="name" v-model="model.name" />
    </div>
    <div>
      <label for="email">Email: </label>
      <input type="email" name="email" id="email" v-model="model.email" />
    </div>
    <div>
      <label for="age">Age: </label>
      <input type="number" name="age" id="age" v-model.number="model.age" />
    </div>
    <div>
      <label for="type">Type: </label>
      <select name="type" id="type" v-model="model.type">
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
        v-model="model.complain"
      />
    </div>
    <div>
      <label for="message">Message: </label>
      <textarea name="message" id="message" v-model="model.message"></textarea>
    </div>
  </form>
</template>
