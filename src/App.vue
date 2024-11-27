<script setup>
import ExpenseTracker from './components/ExpenseTracker.vue'
import ExpenseHistory from './components/ExpenseHistory.vue'
import AddExpense from './components/AddExpense.vue'
import { ref } from 'vue'

let transaction = ref({})
let calculateTransaction = ref({})

const handleTransaction = (e) => {
  transaction.value = e
}

const handleExpense = (e) => {
  calculateTransaction.value = e
  // transaction.value = { ...e }
}
</script>

<template>
  <div class="max-w-md mx-auto text-white h-dvh p-4 text-center bg-white sm:p-8 dark:bg-gray-800">
    <ExpenseTracker :calculateTransaction="calculateTransaction"></ExpenseTracker>
    <ExpenseHistory :transaction="transaction" @handleExpense="handleExpense"></ExpenseHistory>
    <AddExpense @addTransaction="handleTransaction"></AddExpense>
  </div>
</template>

<style></style>
