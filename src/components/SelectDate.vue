<script setup>
import { DatePicker } from 'v-calendar';

const props = defineProps({
  date: Object,
});

const emit = defineEmits(['update:date']);

function onUpdate(value) {
  emit('update:date', value)
}

</script>

<template>
  <h1>Select Date</h1>
  <div>{{ date }}</div>
  <div class="mt-4">
    <DatePicker :modelValue="date" @update:modelValue="onUpdate"/>
  </div>
</template>

<style scoped>
.mt-4 {
  margin-top: 16px;
}
</style>