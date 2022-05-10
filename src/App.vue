<template>
  <div>
    <TodoList></TodoList>
    <CreateTodo></CreateTodo>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoList from "./components/TodoList.vue";
import CreateTodo from "./components/CreateTodo.vue";

@Options({
  components: {
    TodoList,
    CreateTodo,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss"></style>
