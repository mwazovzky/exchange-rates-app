<script setup>
const props = defineProps({
  rate: Object,
});
</script>

<template>
  <h1>Exchange Rate</h1>
  <div class="currency">{{ rate.Currency }}</div>
  <div class="value">{{ rate.Value }}</div>
</template>

<style scoped>
.currency {
  color: #42b983;
  font-weight: bold;
  font-size: 3em;
}
.value {
  font-size: 5em;
}
</style>
