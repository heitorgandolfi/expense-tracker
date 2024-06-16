<script setup>
import { ref } from "vue";

const date = ref(new Date().toLocaleDateString());
</script>

<template>
  <h2>
    Expense Tracker <span>({{ date }})</span>
  </h2>
</template>

<style scoped>
span {
  font-size: 1rem;
  font-weight: 500;
  color: #888;
  margin-left: 10px;
}
</style>
