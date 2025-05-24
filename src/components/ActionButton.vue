<template>
  <button @click="$emit('click')" class="action-button">
    {{ label }}
  </button>
</template>

<script setup>
const props = defineProps({
  label: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
.action-button {
  padding: 10px 15px;
  font-size: 25px;
  background-color:rgb(101, 166, 196);
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
  
  &:hover {
    background-color:rgb(101, 166, 196);
    transform: translateY(-2px);
  }
}
</style>