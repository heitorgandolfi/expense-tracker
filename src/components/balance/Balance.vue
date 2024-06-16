<script setup>
const props = defineProps({
  balance: {
    type: Number,
    required: true,
    default: 0,
  },
});
</script>

<template>
  <h4>Your Balance</h4>
  <h1 id="balance">$ {{ props.balance }}</h1>
</template>
