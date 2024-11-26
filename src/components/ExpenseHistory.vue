<script setup>
import { onUpdated } from 'vue'
import Transaction from './partials/Transaction.vue'
import { ref, watch } from 'vue'

// Define props
const props = defineProps(['transaction'])

const newTransaction = ref({})

// Watch for changes to the prop
// watch(
//   () => props.transaction,
//   (newValue, oldValue) => {
//     console.log('Prop changed from', oldValue, 'to', newValue)
//   },
// )

onUpdated(() => {
  newTransaction.value = props.transaction
})
</script>

<template>
  <div class="mt-8">
    <h4>History</h4>
    <hr class="border-gray-500 border-2 mb-5" />
    <Transaction :transactionText="newTransaction.text" :transactionAmount="newTransaction.amount">
    </Transaction>
  </div>
</template>

<style></style>
