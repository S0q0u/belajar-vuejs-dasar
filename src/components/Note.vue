<script setup>
import {
  onBeforeMount,
  onMounted,
  onUpdated,
  reactive,
  ref,
  useTemplateRef,
} from 'vue';

const notes = reactive([]);
const note = ref('');
// representasi dari elemen input dengan ref noteInput
const noteInput = useTemplateRef('noteInput');
const notesList = useTemplateRef('notesList');

function addNote() {
  notes.push(note.value);
  note.value = '';
  noteInput.value.focus();
  if (notesList.value) {
    notesList.value.forEach((li) => {
      console.log(li.textContent);
    });
  }
}

onBeforeMount(() => {
  console.log('onBeforeMount');
});

onMounted(() => {
  console.log('onMounted');
});

onUpdated(() => {
  console.log('onUpdated');
});
</script>
<template>
  <h1>Buat Note</h1>
  <div>
    <input
      type="text"
      v-model="note"
      ref="noteInput"
      placeholder="Tulis note di sini"
    />
    <button @click="addNote">Add Note</button>
  </div>

  <h1>Daftar Note</h1>
  <ul>
    <li v-for="note in notes" :key="note" ref="notesList">{{ note }}</li>
  </ul>
</template>

<style scoped></style>
