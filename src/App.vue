<script setup>
import { ref, computed } from "vue";

import Header from "./components/header/Header.vue";
import Balance from "./components/balance/Balance.vue";
import IncomeExpense from "./components/incomeExpense/IncomeExpense.vue";
import AddTransaction from "./components/addTransaction/AddTransaction.vue";
import Transactionlist from "./components/transactionList/TransactionList.vue";

let transactions = ref([]);

const handleAddTransaction = (transaction) => {
  transactions.value = [...transactions.value, transaction];
};

const transactionsTotal = computed(() => {
  return transactions.value
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

const incomesTotal = computed(() => {
  const incomes = transactions.value
    .filter((transaction) => {
      return transaction.amount > 0;
    })
    .reduce((acc, income) => {
      return acc + income.amount;
    }, 0);

  return incomes.toFixed(2);
});

const expenseTotal = computed(() => {
  const expenses = transactions.value
    .filter((transaction) => {
      return transaction.amount < 0;
    })
    .reduce((acc, expense) => {
      return acc + expense.amount;
    }, 0);

  return expenses.toFixed(2);
});
</script>

<template>
  <Header />
  <div class="container">
    <Balance :balance="+transactionsTotal" />
    <IncomeExpense :income="+incomesTotal" :expense="+expenseTotal" />
    <Transactionlist :transactions="transactions" />
    <AddTransaction @add-transaction="handleAddTransaction" />
  </div>
</template>

<style scoped></style>
