<script setup></script>

<template>
  <div>
    <h3 class="text-4xl font-bold leading-tight">Expense Tracker</h3>
    <div class="my-8">
      <h4>YOUR BALANACE</h4>
      <h4>$50</h4>
      <!-- {{ Balance }} -->
    </div>
    <div class="inline-flex rounded-lg shadow-sm">
      <span
        class="py-3 px-4 inline-flex items-center gap-x-2 -ms-px first:rounded-s-lg first:ms-0 last:rounded-e-lg font-medium focus:z-10 border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 focus:outline-none focus:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-neutral-900 dark:border-neutral-700 dark:text-white dark:hover:bg-neutral-800 dark:focus:bg-neutral-800 sm:p-5"
      >
        Income
        <span class="text-green-400"> + $100 </span>
      </span>
      <span
        class="py-3 px-4 inline-flex items-center gap-x-2 -ms-px first:rounded-s-lg first:ms-0 last:rounded-e-lg font-medium focus:z-10 border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 focus:outline-none focus:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-neutral-900 dark:border-neutral-700 dark:text-white dark:hover:bg-neutral-800 dark:focus:bg-neutral-800 sm:p-5"
      >
        Expense
        <span class="text-red-400"> - $50</span>
      </span>
    </div>
    <!-- {{ Income }} | {{ Expense }} -->
  </div>
</template>

<style></style>
