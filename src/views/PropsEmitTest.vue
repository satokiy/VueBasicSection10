<template>
  <div>
    PropsEmitTest
    <div>{{ setupBooks }}</div>
    <div>{{ dataBooks }}</div>
    <ul>
      <li v-for="book in setupBooks" :key="book">
        {{ book.title }}
      </li>
    </ul>
    <button @click="emitTest">emitTest click</button>
  </div>
</template>

<script>
export default {
  props: {
    setupBooks: Array,
    dataBooks: Array,
  },

  setup(props, { emit }) {
    console.log(props.setupBooks);
    console.log(props.dataBooks);

    const emitTest = () => {
      emit("custom-event", "emit child value");
    }
    return {
      emitTest,
    };
  },
};
</script>

<style></style>
