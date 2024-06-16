<script>
import Header from "./components/header/Header.vue";
import Balance from "./components/balance/Balance.vue";
import IncomeExpense from "./components/incomeExpense/IncomeExpense.vue";
import Transactionlist from "./components/transactionList/TransactionList.vue";
import AddTransaction from "./components/addTransaction/AddTransaction.vue";

export default {
  components: {
    Header,
    Balance,
    IncomeExpense,
    Transactionlist,
    AddTransaction,
  },
};
</script>

<template>
  <Header />
  <div class="container">
    <Balance />
    <IncomeExpense />
    <Transactionlist />
    <AddTransaction />
  </div>
</template>

<style scoped></style>
