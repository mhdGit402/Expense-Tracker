<script setup>
import Transaction from './partials/Transaction.vue'
import { ref, watch } from 'vue'

// Define props
const props = defineProps(['transaction'])
const emit = defineEmits(['handleExpense'])
const allTransaction = ref([])

// Watch for changes to the props
watch(
  () => [props.transaction.text, props.transaction.amount, props.transaction.type],
  (newValues) => {
    const [text, amount, type] = newValues

    // Create a new transaction object
    const newTransaction = { text, amount, type } // Create a new object here

    // Push the new transaction to the allTransaction array
    allTransaction.value.push(newTransaction) // Push the new object
    emit('handleExpense', allTransaction)
  },
)
</script>

<template>
  <div class="mt-8">
    <h4>History</h4>
    <hr class="border-gray-500 border-2 mb-5" />
    <Transaction :allTransaction="allTransaction"> </Transaction>
  </div>
</template>

<style></style>
