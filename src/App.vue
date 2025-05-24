// src/App.vue
<template>
  <div class="app">
    <h1>IronContacts</h1>
    <table>
      <thead>
        <tr>
          <th>Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won an Oscar</th>
          <th>Won an Emmy</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <td>
            <img
              :src="contact.pictureUrl"
              :alt="`Foto de ${contact.name}`"
              class="profile"
            />
          </td>
          <td>{{ contact.name }}</td>
          <td>{{ contact.popularity.toFixed(2) }}</td>
          <td>
            <span v-if="contact.wonOscar">🏆</span>
          </td>
          <td>
            <span v-if="contact.wonEmmy">🏆</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import allContacts from "./contacts.json";
import { ref } from "vue";
const contacts = ref(allContacts.slice(5, 10));
</script>

<style>
 {
  font-weight: bold;
  font-size: 300px;
  padding: 10px;
}
</style>
