<script setup>
import { computed } from "vue";

const emit = defineEmits(["delete-transaction"]);
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

function getTransactionType(amount) {
  return amount > 0 ? "plus" : "minus";
}

const hasTransactions = computed(() => props.transactions.length > 0);
</script>

<template>
  <div class="transaction-list">
    <h3>History</h3>
    <p v-if="!hasTransactions" class="empty-list">
      You don't have any transactions yet.
    </p>

    <ul v-else id="list" class="list">
      <li
        v-for="{ id, text, amount } in props.transactions"
        :key="id"
        :class="getTransactionType(amount)"
      >
        {{ text }} <span>$ {{ amount }}</span>
        <button class="delete-btn" @click="$emit('delete-transaction', id)">x</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.empty-list {
  text-align: center;
  color: #a19e9e;
}
</style>
