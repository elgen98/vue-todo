<template>
  <div>
    <TodoList></TodoList>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoList from "./components/TodoList.vue";

@Options({
  components: {
    TodoList,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss"></style>
