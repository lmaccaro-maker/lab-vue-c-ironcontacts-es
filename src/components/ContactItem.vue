<template>
  <tr>
    <td>
      <img :src="contact.pictureUrl" :alt="`Foto de ${contact.name}`" class="profile" />
    </td>
    <td>{{ contact.name }}</td>
    <td>{{ contact.popularity.toFixed(2) }}</td>
    <td>
      <span v-if="contact.wonOscar">🏆</span>
    </td>
    <td>
      <span v-if="contact.wonEmmy">🏆</span>
    </td>
    <td>
      <button @click="$emit('delete', contact.id)">Delete</button>
    </td>
  </tr>
</template>

<script setup>
const props = defineProps({
  contact: {
    type: Object,
    required: true
  }
});
</script>

<style scoped>
.profile {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #ccc;
}

button {
  background-color:rgb(101, 166, 196);
  color: #fff;
  padding: 15px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
  
}

button:hover {
  background-color: #c82333;
}
</style>