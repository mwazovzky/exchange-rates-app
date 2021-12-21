<script setup>
import { ref } from 'vue'
import SelectCurrency from '@/components/SelectCurrency.vue'
import SelectDate from '@/components/SelectDate.vue'

const currencies = ["USD", "EUR", "RUB"]
const currency = ref("USD")
const date = ref(new Date())
</script>

<template>
  <SelectCurrency :currencies="currencies" v-model:currency="currency"/>
  <SelectDate :date="date"/>
</template>
