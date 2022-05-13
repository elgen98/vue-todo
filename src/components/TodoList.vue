<template>
  <main>
    <TodoCounter :counter="todoAmount"></TodoCounter>
    <CreateTodo @sendTodo="getTodo($event)"></CreateTodo>
    <ul>
      <li
        v-for="(todo, i) in todoArray"
        :key="i"
        :class="todo.done ? 'checked' : 'unchecked'"
      >
        <input type="checkbox" @click="todo.done = !todo.done" />
        <strong>{{ todo.text }}</strong>
        <button @click="deleteTodo(i)">Delete</button>
      </li>
    </ul>
  </main>
</template>

<script lang="ts">
import { Todo } from "../models/Todo";
import { Options, Vue } from "vue-class-component";
import CreateTodo from "./CreateTodo.vue";
import TodoCounter from "./TodoCounter.vue";
@Options({
  components: {
    CreateTodo,
    TodoCounter,
  },
})
export default class TodoList extends Vue {
  result = "";
  todoArray: Todo[] = [];
  todoAmount = 0;

  getTodo(data: string) {
    this.result = data;
    let newTodo: Todo = new Todo(this.result);
    this.todoArray.push(newTodo);
    this.todoAmount = this.todoArray.length;
    console.log(this.todoArray);
  }

  deleteTodo(i: number) {
    this.todoArray.splice(i, 1);
    this.todoAmount = this.todoArray.length;
  }

  /* checkTodo(itemIndex: number) {
    this.todoArray[itemIndex].done = this.todoArray[itemIndex].done
      ? false
      : true;
  } */
}
</script>

<style lang="scss" scoped>
main {
  margin-top: 10%;
  ul {
    width: 300px;
    padding: 0;

    li {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
        Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
      list-style-type: none;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      gap: 50px;
      word-break: break-all;
      button {
        word-break: keep-all;
        height: 25px;
      }
    }
  }
}
.checked > strong {
  text-decoration-line: line-through;
  opacity: 0.5;
}
</style>
