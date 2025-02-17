<script setup>
import Calculator from "./components/Calculator.vue";
</script>

<template>
  <main>
    <div class="calculator-title">Anton's Calculator</div>
    <Calculator />
  </main>
</template>

<style scoped>
.calculator-title {
  font-size: 40px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 24px;
  text-decoration: underline;
  text-underline-offset: 4px;
  text-decoration-thickness: 2px;
}
</style>
