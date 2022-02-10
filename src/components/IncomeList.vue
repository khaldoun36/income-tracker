<template>
  <div class="income-list">
    <div v-for="item in props.incomeProp" :key="item.id">
      <IncomeItem :item="item" @delete-item="handleEmit" />
    </div>
  </div>
</template>

<script setup>
/******************** */
/*       imports      */
/******************** */

import IncomeItem from "./IncomeItem.vue";

/******************** */
/*     Variables      */
/******************** */

const props = defineProps({
  incomeProp: {
    type: Object,
  },
});

const emit = defineEmits(["emitted-item"]);
/******************** */
/*     Functions      */
/******************** */

const handleEmit = (item) => {
  emit("emitted-item", item);
};
</script>

<style>
.income-list {
  margin-top: var(--size-10);
  padding: var(--size-9);
}
</style>
