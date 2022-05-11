<template>
  <div>
    <CreateTodo @sendTodo="getTodo($event)"></CreateTodo>
    <ul v-for="(todo, i) in todoArray" :key="i">
      <li>{{ todo.text }}</li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Todo } from "../models/Todo";
import { Options, Vue } from "vue-class-component";
import CreateTodo from "./CreateTodo.vue";
@Options({
  components: {
    CreateTodo,
  },
})
export default class TodoList extends Vue {
  result = "";
  todoArray: Todo[] = [];

  getTodo(data: string) {
    this.result = data;
    let newTodo: Todo = new Todo(this.result);
    this.todoArray.push(newTodo);
    console.log(this.todoArray);
  }
}
</script>

<style lang="scss" scoped></style>
