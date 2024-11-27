<script setup>
import { ref } from 'vue'
const transactionText = ref('')
const transactionAmount = ref('')
const emit = defineEmits(['addTransaction'])

const addTransaction = () => {
  const transaction = {
    text: transactionText.value,
    amount: transactionAmount.value,
    type: Number(transactionAmount.value) > 0 ? true : false,
  }
  emit('addTransaction', transaction)
  transactionText.value = ''
  transactionAmount.value = ''
}
</script>

<template>
  <div class="mt-8 mb-5">
    <h4>Add new transaction</h4>
    <hr class="border-gray-500 border-2 mb-5" />

    <form class="max-w-sm mx-auto" @submit.prevent="addTransaction">
      <div class="mb-5">
        <label
          for="transactionText"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Text</label
        >
        <input
          v-model="transactionText"
          type="text"
          id="transactionText"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Enter text..."
        />
      </div>
      <div class="mb-5">
        <label
          for="transactionAmount"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Amount (add - for expense and + for income)</label
        >
        <input
          v-model="transactionAmount"
          type="text"
          id="transactionAmount"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Enter amount..."
        />
      </div>
      <button
        type="submit"
        class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >
        Add transaction
      </button>
    </form>
  </div>
</template>

<style></style>
