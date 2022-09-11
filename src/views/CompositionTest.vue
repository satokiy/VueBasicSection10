<template>
  <div>
    Composition Test
    <p>{{ name }}</p>
    <p>ref: {{ nameRef }}</p>
    <p>{{ age }}</p>
    <p>reactiveToRefs: {{ titleRef }}</p>
    <p>reactiveToRefs: {{ authorRef[1] }}</p>
    <p>computed: {{ totalPrice }}</p>
    <button @click="btnClick">click</button>
    <div>watch: <input v-model="search"></div>
    <div>watchEffect: <input v-model="searchEffect"></div>
  </div>
</template>

<script>
import { reactive, ref, toRefs, computed, watch, watchEffect, onMounted } from "vue";
export default {
  setup() {
    let name = "大谷";
    const age = 230;
    const nameRef = ref("錦織");
    const book = reactive({
      title: "title",
      author: ["大谷", "伊藤"],
    });
    const booktoRefs = reactive({
      titleRef: "title",
      authorRef: ["大谷", "伊藤"],
    });

    const btnClick = (e) => {
      console.log(book.title);
      console.log(e);
    };

    const search = ref('')
    watch(search, (newValue, prevValue) => {
      console.log(`watch: ${search.value}`)
      console.log(`new: ${newValue}`)
      console.log(`prev: ${prevValue}`)
    })

    const searchEffect = ref('')
    watchEffect(() => {
      console.log(`watchEffect: ${searchEffect.value}`)
    })

    onMounted(() => {
      console.log('onMounted')
    })

    const item = reactive({
      price: 100,
      number: 1,
    });

    const totalPrice = computed(() => {
      return item.price * item.number;
    });

    console.log("set up");
    console.log(nameRef);
    console.log(nameRef.value);

    return {
      name,
      age,
      nameRef,
      book,
      ...toRefs(booktoRefs),
      btnClick,
      item,
      totalPrice,
      search,
      searchEffect,
    };
  },
  data() {
    return {
      number: 1,
      sports: "soccer",
    };
  },
  created() {
    console.log("created");
    console.log(this);
  },
  mounted() {
    console.log("mounted");
  },
};
</script>

<style></style>
