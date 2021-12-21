<script setup>
import moment from 'moment'
import { computed, ref, watch } from 'vue'
import SelectCurrency from '@/components/SelectCurrency.vue'
import SelectDate from '@/components/SelectDate.vue'
import ShowRate from '@/components/ShowRate.vue'

const loading = ref(true)
const rates = ref([])
const currency = ref("USD")
const date = ref(new Date())

const currencies = computed(() => rates.value.map(r => r.Currency))
const rate = computed(() => rates.value.find(r => r.Currency == currency.value))
const dateString = computed(() => moment(date.value).format('DD/MM/YYYY'))

watch(dateString, () => fetchRates())

fetchRates()

function fetchRates() {
  const url = `http://localhost:8080/api/rates?date=${dateString.value}`
  fetch(url)
    .then(r => r.json())
    .then(d => {
      rates.value = d
      loading.value = false
    })
}

</script>

<template>
  <SelectCurrency v-if="!loading" :currencies="currencies" v-model:currency="currency"/>
  <SelectDate v-model:date="date"/>
  <ShowRate v-if="!loading" :rate="rate"/>
</template>
