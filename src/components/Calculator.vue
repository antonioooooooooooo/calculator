<script setup>
import Display from "./Display.vue";
import ACButton from "./buttons/ACButton.vue";
import DivideButton from "./buttons/DivideButton.vue";
import MultiplyButton from "./buttons/MultiplyButton.vue";
import DeleteButton from "./buttons/DeleteButton.vue";
import MinusButton from "./buttons/MinusButton.vue";
import PlusButton from "./buttons/PlusButton.vue";
import EqualsButton from "./buttons/EqualsButton.vue";
import ModuloButton from "./buttons/ModuloButton.vue";
import DotButton from "./buttons/DotButton.vue";
import NumberButton from "./buttons/NumberButton.vue";
import { ref } from "vue";

const expression = ref("");
const answer = ref("");

function getLastNumber() {
  const numbers = expression.value.split(/[\+\-÷×%]/);
  const lastNumber = numbers[numbers.length - 1];

  return lastNumber;
}

function formatExpression() {
  return expression.value.replace("÷", "/").replace("×", "*");
}

function handleDotClick() {
  if (answer.value !== "") {
    expression.value = answer.value;
    answer.value = "";

    if (expression.value.indexOf(".") > -1) {
      alert("Invalid input! Only one dot may be in a number.");
      return;
    }

    expression.value += ".";
    return;
  }

  const lastNumber = getLastNumber();

  if (lastNumber.indexOf(".") > -1) {
    alert("Invalid input! Only one dot may be in a number.");
    return;
  }

  expression.value += ".";
}

function handleOperatorClick(operator) {
  if (answer.value !== "") {
    expression.value = answer.value + operator;
    answer.value = "";
    return;
  }

  if (
    expression.value.length == 0 ||
    ["+", "-", "÷", "×", "%"].includes(
      expression.value[expression.value.length - 1]
    )
  ) {
    alert("Invalid input! Operator must come after a number.");
    return;
  }

  expression.value += operator;
}

function handleZeroClick() {
  if (answer.value !== "") {
    expression.value = answer.value;
    answer.value = "";

    if (expression.value === "0") {
      alert("Invalid input! No leading zeros allowed.");
      return;
    }

    expression.value += "0";
    return;
  }

  const lastNumber = getLastNumber();

  if (lastNumber.length == 0 || lastNumber == "0") {
    alert("Invalid input! No leading zeros allowed.");
    return;
  }

  expression.value += "0";
}

function evaluateExpression() {
  const formattedExpression = formatExpression();
  answer.value = eval(formattedExpression).toString();
}
</script>

<template>
  <div class="calculator-wrapper">
    <Display :expression="expression" :answer="answer" />
    <ACButton
      @click="
        expression = '';
        answer = '';
      "
    />
    <DivideButton @click="handleOperatorClick('÷')" />
    <MultiplyButton @click="() => handleOperatorClick('×')" />
    <DeleteButton
      @click="
        answer = '';
        expression = expression.slice(0, -1);
      "
    />
    <MinusButton @click="() => handleOperatorClick('-')" />
    <PlusButton @click="() => handleOperatorClick('+')" />
    <EqualsButton @click="evaluateExpression" />
    <ModuloButton @click="() => handleOperatorClick('%')" />
    <DotButton @click="handleDotClick" />
    <NumberButton
      v-for="n in 9"
      :key="n"
      :value="n"
      :column="n % 3"
      :row="3 + Math.floor((n - 1) / 3)"
      @click="
        expression =
          answer.length > 0 ? answer + n.toString() : expression + n.toString();
        answer = '';
      "
    />
    <NumberButton :value="0" :row="6" :column="2" @click="handleZeroClick" />
  </div>
</template>

<style scoped>
.calculator-wrapper {
  display: grid;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: 200px repeat(5, 100px);
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
  border: 2px solid #383838;
  border-radius: 20px;
  overflow: hidden;
}
</style>
