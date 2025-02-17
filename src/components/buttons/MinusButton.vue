<script setup>
import GenericButton from "./GenericButton.vue";
</script>

<template>
  <GenericButton class="minus-button" text="-" />
</template>

<style scoped>
.minus-button {
  grid-column: 4;
  grid-row: 3;
  background-color: #59bce6;
}
.minus-button:hover {
  background-color: #69a8e8;
}
</style>
