<template>
  <div class="income-item">
    <div class="remove-item" @click="handleClick(item.id)">Delete</div>
    <div class="edit-item">Edit</div>
    <div class="desc">{{ item.desc }}</div>
    <div class="price">{{ item.incomeValue }}</div>
    <div class="date">{{ formatedDate }}</div>
  </div>
</template>

<script setup>
/******************** */
/*       imports      */
/******************** */

/******************** */
/*     Variables      */
/******************** */

const props = defineProps({
  item: {
    type: Object,
  },
});

const date = new Date(props.item.date);

const month = date.toLocaleString("en-US", { month: "long" }); // December
const day = date.toLocaleString("en-US", { day: "numeric" }); // 9
const year = date.toLocaleString("en-US", { year: "numeric" }); // 2019

const formatedDate = `${day} - ${month} - ${year}`;

const emit = defineEmits(["delete-item"]);
/******************** */
/*     Functions      */
/******************** */

const handleClick = (item) => {
  emit("delete-item", item);
};
</script>

<style>
.income-item {
  /* position: relative; */
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--size-3) var(--size-3) var(--size-3) 0px;
  background-color: var(--gray-3);
  border-radius: var(--radius-2);
  /* max-width: 600px; */
  margin: 0 auto 30px;
  font-size: var(--font-size-2);
}
.remove-item,
.edit-item {
  cursor: pointer;
  color: var(--red-5);
  font-weight: var(--font-weight-6);
  line-height: var(--font-lineheight-00);
  text-align: center;
}

.remove-item {
  padding: 0 var(--size-6) 0 var(--size-2);
}

.edit-item {
  color: var(--blue-5);
  padding: 0 var(--size-2) 0 var(--size-2);
}
.desc,
.price,
.date {
  color: var(--gray-6);
}

.price {
  min-width: 100px;
}
.date {
  text-align: right;
}
</style>
