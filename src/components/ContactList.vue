<template>
  <div>
    <div class="button-group">
      <ActionButton label="Add Random Contact" @click="addRandomContact" />
      <ActionButton label="Sort by Name" @click="sortByName" />
      <ActionButton label="Sort by Popularity" @click="sortByPopularity" />
    </div>
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
        <ContactItem 
          v-for="contact in displayedContacts" 
          :key="contact.id"
          :contact="contact"
          @delete="deleteContact"
        />
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from "vue";
import allContacts from "../contacts.json";
import ContactItem from './ContactItem.vue';
import ActionButton from './ActionButton.vue';

const displayedContacts = ref(allContacts.slice(0, 5));
const remainingContacts = ref(allContacts.slice(5));

function addRandomContact() {
  if (remainingContacts.value.length > 0) {
    const randomIndex = Math.floor(Math.random() * remainingContacts.value.length);
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
  displayedContacts.value = displayedContacts.value.filter(
    contact => contact.id !== id
  );
}
</script>

<style scoped>
.button-group {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 20px;
}

button {
  display: inline-block;
  padding: 12px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color:rgb(101, 166, 196);
  color: white;
  border: none;
  margin: 0 0 60px 0;
  border-radius: 5px;
  transition: background-color 0.3s, transform 0.2s;
}

button:hover {
  background-color:rgb(101, 166, 196);
  color: #fff;
  transform: translateY(-2px);
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

th {
  background-color:rgb(101, 166, 196);
  color: #fff;
  font-weight: bold;
  font-size: 30px;
  padding: 15px;
  text-align: center;
  border-bottom: 3px solid #0056b3;
}

td {
  font-size: 70px;
  padding: 10px;
  text-align: center;
  border: 1px solid #ddd;
  background-color: #f8f9fa;
}

tr:nth-child(even) {
  background-color: #f1f1f1;
}

tr:hover {
  background-color: #e9f5ff;
}

.profile {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #ccc;
}
</style>