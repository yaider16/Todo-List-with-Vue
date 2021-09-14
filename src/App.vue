<template>
  <TodoApp/>
</template>

<script>

export default{
  name: "App",
  components: {
    TodoApp
  }
}

import TodoApp from "./components/TodoApp.vue"
import { ref } from "vue"
import Test from "./components/Test.vue"
import Car from "./components/Car.vue"
</script>

<style lang="css" scoped>
</style>