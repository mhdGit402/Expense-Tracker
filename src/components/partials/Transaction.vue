<script setup>
// Define props
const props = defineProps({
  allTransaction: {
    type: Object,
  },
})
</script>

<template>
  <div>
    <!-- consider delete for each transaction -->
    <ul class="mt-3 flex flex-col">
      <li
        v-for="transaction in allTransaction"
        :key="transaction.text"
        :class="[
          transaction.type ? 'income' : 'expense',
          'bg-white text-black inline-flex items-center gap-x-2 py-3 px-4 text-sm border -mt-px first:rounded-t-lg first:mt-0 last:rounded-b-lg dark:border-neutral-700]',
        ]"
      >
        <div class="flex items-center justify-between w-full">
          <span>{{ transaction.text }}</span>
          <span>$ {{ transaction.amount }}</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<style></style>
