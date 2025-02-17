<script setup>
import GenericButton from "./GenericButton.vue";

defineProps({
  value: {
    type: Number,
    required: true,
  },
  column: {
    type: Number,
    required: true,
  },
  row: {
    type: Number,
    required: true,
  },
});
</script>

<template>
  <GenericButton
    :text="value.toString()"
    :style="{ gridColumn: column, gridRow: row }"
  />
</template>
