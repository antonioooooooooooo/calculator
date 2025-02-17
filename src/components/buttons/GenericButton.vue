<script setup>
defineProps({
  text: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <button class="generic-button">{{ text }}</button>
</template>

<style scoped>
.generic-button {
  background-color: #db8ca0;
  color: white;
  transition: background-color 0.1s ease-in;
  cursor: pointer;
  font-size: 24px;
  border: none;
}
.generic-button:active {
  outline: none;
}
.generic-button:hover {
  background-color: #d97a83;
}
</style>
