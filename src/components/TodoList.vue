<template>
  <div>
    <CreateTodo @sendTodo="getTodo($event)"></CreateTodo>
    <ul>
      <li
        v-for="(todo, i) in todoArray"
        :key="i"
        :class="todo.done ? 'checked' : 'unchecked'"
      >
        {{ todo.text }}
        <input type="checkbox" @click="todo.done = !todo.done" />
        <button @click="this.todoArray.splice(i, 1)">Delete</button>
      </li>
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

  /* deleteTodo(i: number) {
    this.todoArray.splice(i, 1);
  } */

  /* checkTodo(itemIndex: number) {
    this.todoArray[itemIndex].done = this.todoArray[itemIndex].done
      ? false
      : true;
  } */
}
</script>

<style lang="scss" scoped>
.checked {
  text-decoration-line: line-through;
  opacity: 0.5;
}
</style>
