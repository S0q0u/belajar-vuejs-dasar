<script setup>
import { provide, reactive } from 'vue';
import Profile from './Profile.vue';
import ProfileAddress from './ProfileAddress.vue';

const profile = reactive({
  name: 'Na Jaemin',
  email: 'inimail@gmail.com',
});

provide('profile', profile);
</script>

<template>
  <input
    v-model="profile.name"
    type="text"
    name="nama"
    id="nama"
    placeholder="name"
  />
  <Profile />
  <ProfileAddress />
</template>

<style scoped></style>
