<script setup>
const props = defineProps({
  income: {
    type: Number,
    required: true,
    default: 0,
  },
  expense: {
    type: Number,
    required: true,
    default: 0,
  },
});
</script>

<template>
  <div class="inc-exp-container">
    <div>
      <h4>Incomes</h4>
      <p id="money-plus" class="money plus">${{ props.income }}</p>
    </div>
    <div>
      <h4>Expenses</h4>
      <p id="money-minus" class="money minus">${{ props.expense }}</p>
    </div>
  </div>
</template>
