<script setup>
import GenericButton from "./GenericButton.vue";
</script>

<template>
  <GenericButton class="delete-button" text="DEL" />
</template>

<style scoped>
.delete-button {
  grid-column: 4;
  grid-row: 2;
  background-color: #59bce6;
}
.delete-button:hover {
  background-color: #69a8e8;
}
</style>
