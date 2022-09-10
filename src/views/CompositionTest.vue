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
  </div>
</template>

<script>
  import { reactive, ref, toRefs, computed } from 'vue'
export default {

  setup(){
    let name = '大谷'
    const age = 230;
    const nameRef = ref('錦織')
    const book = reactive({
      title: 'title',
      author: ['大谷','伊藤']
    })
    const booktoRefs = reactive({
      titleRef: 'title',
      authorRef: ['大谷','伊藤']
    })

    const btnClick = e => {
      console.log(book.title)
      console.log(e)
    }

    const item = reactive({
      price: 100,
      number: 1
    })
  
    const totalPrice = computed( () => {
      return item.price * item.number;
    })

    console.log('set up');
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
      totalPrice
    }
  },
  data(){
    return {
      number: 1,
      sports: 'soccer'
    }
  },
  created() { 
    console.log('created')
    console.log(this);
  },
  mounted() { console.log('mounted') },

}
</script>

<style>

</style>