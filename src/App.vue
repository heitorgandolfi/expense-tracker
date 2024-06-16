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

const incomesTotal = computed(() => {
  const incomes = transactions.value
    .filter((transaction) => {
      return transaction.amount > 0;
    })
    .reduce((acc, income) => {
      return acc + income.amount;
    }, 0);

  return incomes;
});

const expenseTotal = computed(() => {
  const expenses = transactions.value
    .filter((transaction) => {
      return transaction.amount < 0;
    })
    .reduce((acc, expense) => {
      return acc + expense.amount;
    }, 0);

  return expenses;
});
</script>

<template>
  <Header />
  <div class="container">
    <Balance :balance="transactionsTotal" />
    <IncomeExpense :income="incomesTotal" :expense="expenseTotal" />
    <Transactionlist :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<style scoped></style>
