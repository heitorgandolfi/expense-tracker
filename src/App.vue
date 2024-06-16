<script setup>
import Header from "./components/header/Header.vue";
import Balance from "./components/balance/Balance.vue";
import IncomeExpense from "./components/incomeExpense/IncomeExpense.vue";
import Transactionlist from "./components/transactionList/TransactionList.vue";
import AddTransaction from "./components/addTransaction/AddTransaction.vue";

import { ref, computed } from "vue";

const transactions = ref([
  {
    id: 1,
    text: "Cash",
    amount: -400,
  },
  {
    id: 2,
    text: "Book",
    amount: -20,
  },
  {
    id: 3,
    text: "Salary",
    amount: 1000,
  },
]);

const transactionsTotal = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
</script>

<template>
  <Header />
  <div class="container">
    <Balance :balance="transactionsTotal" />
    <IncomeExpense />
    <Transactionlist :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<style scoped></style>
