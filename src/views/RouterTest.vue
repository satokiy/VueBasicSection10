<template>
  <div>RouterTest

    <button @click="goHome">return Home</button>
    <button @click="checkRoutePath">check Route</button>
  </div>
</template>

<script>
import { useRoute, useRouter, onBeforeRouteLeave } from "vue-router";
export default {
  setup() {
    const route = useRoute()
    const router = useRouter()

    const goHome = () => {
      router.push('/')
    }
    const checkRoutePath = () => {
      console.log(route.path)
    }

    onBeforeRouteLeave((to, from) => {
      console.log(`to: ${to}`)
      console.log(`from: ${from}`)
    })

    return {
      goHome,
      checkRoutePath,
    }
  },
};
</script>

<style></style>
