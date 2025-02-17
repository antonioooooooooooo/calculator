<script setup>
import GenericButton from "./GenericButton.vue";
</script>

<template>
  <GenericButton class="equals-button" text="=" />
</template>

<style scoped>
.equals-button {
  grid-column: 4;
  grid-row: 5 / span 2;
  background-color: #59bce6;
}
.equals-button:hover {
  background-color: #69a8e8;
}
</style>
