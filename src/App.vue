<template>
  <div class="app">
    <h1>IronContacts</h1>
    <ContactList />
  </div>
</template>

<script setup>
import ContactList from "./components/ContactList.vue";
</script>

<style scoped>
.app {
  padding: 20px;
  font-family: "Arial", sans-serif;
}

h1 {
  text-align: center;
  background-color:white;
  color: rgb(40, 127, 167);
  font-size: 50px;
  margin: 0 0 80px 0;
}
</style>
