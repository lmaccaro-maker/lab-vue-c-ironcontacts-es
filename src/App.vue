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
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <td><img :src="contact.pictureUrl" :alt="`Foto de ${contact.name}`" class="profile" /></td>
          <td>{{ contact.name }}</td>
          <td>{{ contact.popularity.toFixed(2) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import contacts from "./contacts.json";
import { ref } from 'vue'

</script>

<style>
 {
  background-color:; 
  font-weight: bold;
  font-size:200px;
  padding: 10px; 
  
}

</style>
