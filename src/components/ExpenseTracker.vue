<script setup>
import { ref, defineProps, watch, toRaw } from 'vue'

const prop = defineProps(['calculateTransaction'])
let transactionArray
let incomeArray
let expenseArray
let income = ref(0)
let expense = ref(0)
let balance = ref(0)

watch(
  () => prop.calculateTransaction,
  (newValue) => {
    transactionArray = toRaw(newValue._rawValue)
    // Step 1: Extract amounts and convert to numbers
    const amounts = transactionArray.map((item) => Number(item.amount))

    // Step 2: Separate into positive and negative arrays
    incomeArray = amounts.filter((num) => num > 0)
    expenseArray = amounts.filter((num) => num < 0).map((num) => Math.abs(num)) // Convert negatives to positives

    // Step 3: Perform addition
    income.value = incomeArray.reduce((acc, num) => acc + num, 0)
    expense.value = expenseArray.reduce((acc, num) => acc + num, 0)
    balance.value = income.value - expense.value
  },
  { deep: true },
  // Use with Caution
  // Deep watch requires traversing all nested properties in the watched object,
  // and can be expensive when used on large data structures.
  // Use it only when necessary and beware of the performance implications.
)
</script>

<template>
  <div>
    <h3 class="text-4xl font-bold leading-tight">Expense Tracker</h3>
    <div class="my-8">
      <h4>YOUR BALANACE</h4>
      <h4>${{ balance }}</h4>
    </div>
    <div class="inline-flex rounded-lg shadow-sm">
      <span
        class="py-3 px-4 inline-flex items-center gap-x-2 -ms-px first:rounded-s-lg first:ms-0 last:rounded-e-lg font-medium focus:z-10 border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 focus:outline-none focus:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-neutral-900 dark:border-neutral-700 dark:text-white dark:hover:bg-neutral-800 dark:focus:bg-neutral-800 sm:p-5"
      >
        Income
        <span class="text-green-400"> + ${{ income }} </span>
      </span>
      <span
        class="py-3 px-4 inline-flex items-center gap-x-2 -ms-px first:rounded-s-lg first:ms-0 last:rounded-e-lg font-medium focus:z-10 border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 focus:outline-none focus:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-neutral-900 dark:border-neutral-700 dark:text-white dark:hover:bg-neutral-800 dark:focus:bg-neutral-800 sm:p-5"
      >
        Expense
        <span class="text-red-400"> - ${{ expense }}</span>
      </span>
    </div>
  </div>
</template>

<style></style>
