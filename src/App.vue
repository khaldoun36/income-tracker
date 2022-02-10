<template>
  <VueHeader :totalIncome="totalIncome" />
  <div class="container">
    <VueForm @add-income="addIncome" />
    <IncomeList :incomeProp="income" @emitted-item="deleteItem" />
  </div>
</template>
<script setup>
/******************** */
/*       imports      */
/******************** */
import { computed, ref } from "vue";
import VueHeader from "./components/VueHeader.vue";
import VueForm from "./components/VueForm.vue";
import { v4 as uuidv4 } from "uuid";
import IncomeList from "./components/IncomeList.vue";

/******************** */
/*     Variables      */
/******************** */

const income = ref([
  {
    id: uuidv4(),
    desc: "Web Development task",
    incomeValue: 1000,
    date: 1632611410322,
  },
  {
    id: uuidv4(),
    desc: "Web Design task",
    incomeValue: 3000,
    date: 1667644480322,
  },
]);

/******************** */
/*     Functions      */
/******************** */

const totalIncome = computed(() => {
  let temp = 0;
  if (income.value.length > 0) {
    income.value.forEach((item) => {
      temp += item.incomeValue;
    });
  }

  return temp;
});

const addIncome = (formData) => {
  income.value = [
    ...income.value,
    {
      id: uuidv4(),
      desc: formData.desc,
      incomeValue: formData.incomeValue,
      date: formData.date,
    },
  ];
};

const deleteItem = (id) => {
  income.value = income.value.filter((item) => item.id !== id);
  console.log(income.value);
};
</script>

<style></style>
