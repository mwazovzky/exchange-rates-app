<script setup>
const props = defineProps({
  currencies: Array,
  currency: String,
});

const emit = defineEmits(['update:currency']);

function onChange(event) {
  emit('update:currency', event.target.value)
}

</script>

<template>
  <h1>Select Currency</h1>
  <select :value="currency" @change="onChange">
    <option v-for="item in currencies" :value="item">{{item}}</option>
  </select>
</template>

<style scoped>
select {
  padding: 5px;
  border: 1px solid rgb(222,222,222);
  border-radius: 4px;
}
</style>
