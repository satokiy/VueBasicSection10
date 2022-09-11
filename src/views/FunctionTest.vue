<template>
  <div>
    FunctionTest
    <div>
      <p>item_name: {{ item.name }}</p>
      <p>amount: {{ item.amount }}</p>
      <p>totalPrice: {{ totalPrice }}</p>
      <button @click="increment">+</button>
      <button @click="decrement">-</button>
    </div>
  </div>
</template>

<script>
import { reactive } from "vue";
import useCounter from '@/composables/useCounter'
export default {
  setup() {
    const item = reactive({
      name: "item name",
      price: 100,
      amount: 1,
    });

    const { increment, decrement, totalPrice } = useCounter(item);

    return {
      item,
      increment,
      decrement,
      totalPrice,
    };
  },
};
</script>

<style></style>
