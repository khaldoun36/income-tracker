<template>
  <header class="primary-header">
    <h1>Income Tracker</h1>
    <div class="total-income">$ {{ props.totalIncome }}</div>
  </header>
</template>

<script setup>
/******************** */
/*       imports      */
/******************** */

/******************** */
/*     Variables      */
/******************** */

const props = defineProps({
  totalIncome: {
    type: Number,
  },
});

/******************** */
/*     Functions      */
/******************** */
</script>

<style>
.primary-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--size-3) var(--size-7);
  background-color: var(--gray-9);
  border-bottom: 5px solid var(--yellow-5);
  color: var(--gray-2);
}

.primary-header > h1 {
  font-size: var(--font-size-5);
}

.total-income {
  background-color: var(--yellow-5);
  font-size: var(--font-size-4);
  font-weight: var(--font-weight-9);
  padding: var(--size-2) var(--size-5);
  min-width: var(--size-11);
  text-align: center;
  border-radius: var(--radius-2);
  box-shadow: var(--shadow-4);
}
</style>
