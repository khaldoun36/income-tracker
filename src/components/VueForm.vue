<template>
  <form @submit.prevent="formHandler">
    <input
      type="text"
      placeholder="Description..."
      v-model="formData.desc"
      required
    />
    <input
      type="number"
      placeholder="Value..."
      v-model="formData.incomeValue"
      required
    />
    <input type="date" placeholder="Date" v-model="formData.date" required />
    <input type="submit" value="Submit" />
  </form>
</template>

<script setup>
/******************** */
/*       imports      */
/******************** */

import { ref } from "vue";

/******************** */
/*     Variables      */
/******************** */

const formData = ref({
  desc: null,
  incomeValue: null,
  date: null,
});

const emit = defineEmits(["add-income"]);

/******************** */
/*     Functions      */
/******************** */

const formHandler = () => {
  const formatedDate = new Date(formData.value.date);

  emit("add-income", {
    desc: formData.value.desc,
    incomeValue: formData.value.incomeValue,
    date: formatedDate.getTime(),
  });

  formData.value.desc = null;
  formData.value.incomeValue = null;
  formData.value.date = null;
};
</script>

<style>
form {
  display: flex;
  justify-content: center;
  margin-top: var(--size-8);
}
form input {
  color: var(--gray-6);
  border: none;
  outline: none;
  font-size: var(--font-size-4);
}
form input::placeholder {
  color: var(--gray-6);
}
form input:not([type="submit"]) {
  display: block;
  background: var(--gray-3);
  border: none;
  outline: none;
  padding: var(--size-2) var(--size-3);
}
form input[type="submit"] {
  display: block;
  background: none;
  border: none;
  outline: none;
  color: var(--gray-1);
  font-weight: var(--font-weight-5);
  padding: var(--size-2) var(--size-3);
  background-color: var(--yellow-5);
  cursor: pointer;
}
form input:first-of-type {
  border-radius: var(--radius-2) 0px 0px var(--radius-2);
}
form input:last-of-type {
  border-radius: 0px var(--radius-2) var(--radius-2) 0px;
}

/* ******************************* */
input[type="date"]::-webkit-calendar-picker-indicator {
  cursor: pointer;
  border-radius: 4px;
  margin-right: 2px;
  opacity: 0.6;
  filter: invert(0.8);
}

input[type="date"]::-webkit-calendar-picker-indicator:hover {
  opacity: 1;
}
</style>
