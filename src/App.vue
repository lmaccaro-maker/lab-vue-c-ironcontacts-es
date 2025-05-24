// src/App.vue
<template>
  <div class="app">
    <h1>IronContacts</h1>
    <button @click="addRandomContact">Add Random Contact</button>
    <button @click="sortByName">Sort by Name</button>
    <button @click="sortByPopularity">Sort by Popularity</button>
    <table>
      <thead>
        <tr>
          <th>Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won an Oscar</th>
          <th>Won an Emmy</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in displayedContacts" :key="contact.id">
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
          <td><button @click="deleteContact(contact.id)">Delete</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import allContacts from "./contacts.json";
import { ref } from "vue";
const displayedContacts = ref(allContacts.slice(5, 10));
const remainingContacts = ref(allContacts.slice(5));

function addRandomContact() {
  if (remainingContacts.value.length > 0) {
    const randomIndex = Math.floor(
      Math.random() * remainingContacts.value.length
    );
    const randomContact = remainingContacts.value[randomIndex];
    displayedContacts.value.push(randomContact);
    remainingContacts.value.splice(randomIndex, 1);
  }
}
function sortByName() {
  displayedContacts.value.sort((a, b) => a.name.localeCompare(b.name));
}

function sortByPopularity() {
  displayedContacts.value.sort((a, b) => b.popularity - a.popularity);
}

function deleteContact(id) {
  displayedContacts.value = displayedContacts.value.filter(contact => contact.id !== id);
}

</script>

<style scoped>
h1 {
  text-align: center;
  background-color:rgb(74, 169, 184);
  color: white;
  font-size: 50px;
  margin: 0 0 20px 0;
}


button {
  display: inline-block;
  margin: 20px 20px 20px 0;
  padding: 15px 25px;
  font-size: 16px;
  cursor: pointer;
  background-color: #17a2b8; /* Cambia a tono azul */
  color: #fff;
  border: none;
  border-radius: 5px;
  transition: background-color 0.3s, transform 0.2s;
}

button:hover {
  background-color: #138496; /* Ajuste para un tono más oscuro en hover */
  transform: translateY(-2px); /* Levanta el botón al pasar sobre él */
}

/* Relleno y color para las filas de la tabla */
tr {
  background-color: #fff;
  border-bottom: 1px solid #ccc;
}

/* Encabezados de la tabla con color e interlineado */
th {
  background-color:rgb(34, 124, 149);
  color: #f8f9fa;
  font-weight: bold;
  font-size: 22px;
  padding: 16px;
  text-align: center;
  border-bottom: 3px solid #495057;
}

/* Celdas de datos con diferente tono y alineación */
td {
  font-size: 20px;
  padding: 16px;
  text-align: center;
  border: 1px solid #ccc;
  vertical-align: middle;
  background-color: #f8f9fa;
}

/* Tabla con fondo degradado sutil para un efecto de transición */
table {
  width: 100%;
  border-collapse: collapse;
  background: linear-gradient(to bottom, #e3f2fd, #fff);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Alternancia de color para filas con sombra */
tr:nth-child(even) {
  background-color: #edf2f7;
}

/* Fondo de las filas ampliado con sombreado */
tr {
  transition: background-color 0.3s;
}
tr:hover {
  background-color: #d0e8f2;
  box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.1);
}

/* Estilos para la imagen de perfil */
.profile {
  width: 48px;
  height: 48px;
  border-radius: 24px;
  object-fit: cover;
  border: 2px solid #adb5bd;
}
</style>
