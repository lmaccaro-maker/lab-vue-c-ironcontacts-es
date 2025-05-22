// src/App.vue
<template>
  <div class="app">
    <h1>Iron Contacts</h1>
    <ul>
      <!-- Usa v-for para iterar sobre los contactos y mostrar información -->
      <li v-for="contact in contacts" :key="contact.id">
        <img
          :src="contact.pictureUrl"
          alt="Image de {{ contact.name }}"
          class="profile"
        />
        <h2>{{ contact.name }}</h2>
        <p>Popularity: {{ contact.popularity }}</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
import contacts from "./contacts.json";
</script>

<style></style>
