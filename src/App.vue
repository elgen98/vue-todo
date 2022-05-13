<template>
  <TodoList></TodoList>
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

<style lang="scss">
body {
  height: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  background-color: #e6d374;
}
</style>
