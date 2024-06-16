<script setup>
import { ref } from "vue";
import { useToast } from "vue-toast-notification";
import "vue-toast-notification/dist/theme-sugar.css";

const transactionText = ref("");
const transactionAmount = ref(null);

const emit = defineEmits(["add-transaction"]);

const $toast = useToast();

const handleAddTransaction = () => {
  if (!transactionText.value || !transactionAmount.value) {
    return $toast.error("Please enter text and amount");
  }

  if (isNaN(transactionAmount.value)) {
    return $toast.error("Please enter a valid number");
  }

  if (transactionAmount.value === 0) {
    return $toast.error("Please enter a non-zero value");
  }

  const newTransaction = {
    id: Math.floor(Math.random() * 100000000),
    text: transactionText.value,
    amount: parseFloat(transactionAmount.value),
  };

  emit("add-transaction", newTransaction);

  transactionText.value = "";
  transactionAmount.value = null;

  $toast.success("Transaction added successfully");
};
</script>

<template>
  <div>
    <h3>Add new transaction</h3>

    <form @submit.prevent="handleAddTransaction">
      <div class="form-control">
        <label for="text">Text</label>
        <input
          type="text"
          id="text"
          placeholder="Enter text..."
          v-model="transactionText"
        />
      </div>

      <div class="form-control">
        <label for="amount"
          >Amount <br />
          (negative value for expense, positive for income)
        </label>

        <input
          type="number"
          id="amount"
          placeholder="Enter amount..."
          v-model="transactionAmount"
        />
      </div>

      <button class="btn">Add transaction</button>
    </form>
  </div>
</template>
