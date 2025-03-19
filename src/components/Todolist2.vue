<script setup>
import { reactive, ref, useTemplateRef } from 'vue';

const Todos = reactive([
  {
    id: 1,
    text: 'Belajar Vue 3',
    completed: true,
  },
  {
    id: 2,
    text: 'Belajar Vue Router',
    completed: false,
  },
  {
    id: 3,
    text: 'Belajar Pinia',
    completed: false,
  },
]);

const newTodo = ref('');
const input = useTemplateRef('input');

function addTodo() {
  Todos.push({
    id: Todos.length + 1,
    text: newTodo.value,
    completed: false,
  });
  newTodo.value = '';
  input.value.focus();
}

function deleteTodo(index) {
  Todos.splice(index, 1);
}

const editedTodo = ref(null);
const editedText = ref('');

function editTodo(todo) {
  editedTodo.value = todo; // Set item yang sedang diedit
  editedText.value = todo.text; // Ambil teks awal
}

function saveEdit(todo) {
  if (editedText.value.trim()) {
    todo.text = editedText.value; // Simpan teks baru ke item
  }
  editedTodo.value = null; // Keluar dari mode edit
}

function cancelEdit() {
  editedTodo.value = null; // Batalkan edit
}
</script>

<template>
  <h1>Todo List</h1>
  <label for="todo">Masukkan To-do Baru: </label>
  <input
    type="text"
    id="todo"
    ref="input"
    @keyup.enter="addTodo"
    v-model="newTodo"
  />
  <button @click="addTodo">Add</button>

  <!-- untuk setiap todo dan indexnya dalam array -->
  <div v-for="(todo, index) in Todos" :key="todo.id">
    <ul>
      <!-- binding class completed kalau completed bernilai true -->
      <li :class="{ completed: todo.completed }">
        <!-- binding id checkbox dengan todo.id,  menghubungkan status todo (kalau checked maka completed bernilai true dan sebaliknya)-->
        <input type="checkbox" :id="todo.id" v-model="todo.completed" />

        <!-- tampilkan tiap text berdasarkan todo.id dan button delete -->
        <!-- Jika sedang diedit, tampilkan input -->
        <template v-if="editedTodo === todo">
          <input v-model="editedText" @keyup.enter="saveEdit(todo)" />
          <button @click="saveEdit(todo)">Save</button>
          <button @click="cancelEdit">Cancel</button>
        </template>

        <!-- Jika tidak dalam mode edit, tampilkan teks biasa -->
        <template v-else>
          <label :for="todo.id">{{ todo.text }}</label>
          <button @click="editTodo(todo)">Edit</button>
          <button @click="deleteTodo(index)">Delete</button>
        </template>
      </li>
    </ul>
  </div>
</template>

<style scoped>
li {
  list-style: none;
}

.completed {
  text-decoration: line-through;
  color: red;
}
</style>
