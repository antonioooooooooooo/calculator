<script setup>
import GenericButton from "./GenericButton.vue";
</script>

<template>
  <GenericButton class="plus-button" text="+" />
</template>

<style scoped>
.plus-button {
  grid-column: 4;
  grid-row: 4;
  background-color: #59bce6;
}
.plus-button:hover {
  background-color: #69a8e8;
}
</style>
