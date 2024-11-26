<script setup>
import { ref, onUpdated, watch } from 'vue'

// let newTransaction = {}
const allTransaction = ref([])

// Define props
const props = defineProps({
  transactionText: {
    type: String,
  },
  transactionAmount: {
    type: String,
  },
})

// Watch for changes to the props
watch(
  () => [props.transactionText, props.transactionAmount],
  (newValues) => {
    const [text, amount] = newValues

    // Create a new transaction object
    const newTransaction = { text, amount } // Create a new object here

    // Push the new transaction to the allTransaction array
    allTransaction.value.push(newTransaction) // Push the new object
    console.log(allTransaction) // Log the current state of allTransaction
  },
)

// onUpdated(() => {
//   let newTransaction = {}
//   newTransaction.text = props.transactionText
//   newTransaction.amount = props.transactionAmount
//   console.log(newTransaction)

//   allTransaction.value.push(newTransaction)
//   console.log(allTransaction)
// })
</script>

<template>
  <div>
    <!-- consider delete for each transaction -->
    <!-- consider different border for income and expense -->
    <!-- {{ transactionText }} | {{ transactionAmount }} -->
    <ul class="mt-3 flex flex-col">
      <li
        v-for="transaction in allTransaction"
        :key="transaction.text"
        class="bg-white text-black inline-flex items-center gap-x-2 py-3 px-4 text-sm border -mt-px first:rounded-t-lg first:mt-0 last:rounded-b-lg dark:border-neutral-700"
      >
        <div class="flex items-center justify-between w-full">
          <span>{{ transaction.text }}</span>
          <span>$ {{ transaction.amount }}</span>
        </div>
      </li>
    </ul>
    <!-- End List Group -->
  </div>
</template>

<style></style>
