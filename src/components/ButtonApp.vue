<script setup>
import Container from './Container.vue';
import MyButton from './MyButton.vue';

function clickHandler() {
  alert('Button clicked');
}
</script>

<template>
  <!-- ini fallthrough attribute karena cuma ada satu atau single element di My Button -->
  <Container title="Contoh Button">
    <!-- semua atribut yang dikirim akan disimpan di variabel attributes -->
    <template #header="attributes">
      <h1>Button App: {{ attributes.counter }}</h1>
    </template>
    <template v-slot:default="attributes">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore modi
        blanditiis doloremque exercitationem, corporis aperiam similique, natus
        ex voluptatem molestias quia enim odio impedit porro fugiat autem
        provident, saepe fuga!
      </p>
      <MyButton
        class="button"
        @click="clickHandler"
        :name="attributes.counter"
      />
    </template>
    <template #footer>
      <p>Copyright 2025 @Harlin Ajeng Ukirasih</p>
    </template>
  </Container>
</template>

<style scoped>
.button {
  background-color: blue;
  color: white;
  padding: 10px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
}
</style>
