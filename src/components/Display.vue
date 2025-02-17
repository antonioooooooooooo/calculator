<script setup>
defineProps({
  expression: {
    type: String,
    required: true,
  },
  answer: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="display-wrapper">
    <div
      class="expression-wrapper"
      :class="{ 'expression-wrapper-with-answer': answer.length > 0 }"
    >
      {{ expression }}
    </div>
    <div v-if="answer.length > 0" class="answer-wrapper">{{ answer }}</div>
  </div>
</template>

<style scoped>
.display-wrapper {
  grid-column: 1 / span 4;
  grid-row: 1;
  background-color: #383838;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-end;
  padding: 20px;
  gap: 12px;
  user-select: none;
}
.expression-wrapper {
  font-size: 32px;
  color: white;
}
.expression-wrapper-with-answer {
  font-size: 24px;
  color: #c2c2c2;
}
.answer-wrapper {
  color: white;
  font-size: 32px;
}
</style>
