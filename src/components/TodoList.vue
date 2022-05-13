<template>
  <main>
    <TodoCounter :counter="todoAmount"></TodoCounter>
    <CreateTodo @sendTodo="getTodo($event)"></CreateTodo>
    <ul>
      <li v-for="(todo, i) in todoArray" :key="i">
        <label class="checkbox-label">
          <input type="checkbox" @click="todo.done = !todo.done" />
          <span class="checkbox-custom"></span>
        </label>
        <strong :class="todo.done ? 'checked' : 'unchecked'">{{
          todo.text
        }}</strong>
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
      border-bottom: 1px solid #998a3d;
      margin-bottom: 10px;
      input {
        position: absolute;
        opacity: 0;
      }

      .checkbox-label .checkbox-custom {
        position: absolute;
        cursor: pointer;
        height: 18px;
        width: 18px;
        background-color: transparent;
        border-radius: 50%;
        border: 2px solid white;
        transition: all 0.1s ease-out;
      }
      .checkbox-label .checkbox-custom::after {
        position: absolute;
        content: "";
        height: 0px;
        width: 0px;
        border-radius: 50%;
        border: solid #e6d374;
        border-width: 0 3px 3px 0;
        -webkit-transform: rotate(0deg) scale(0);
        -ms-transform: rotate(0deg) scale(0);
        transform: rotate(0deg) scale(0);
        opacity: 1;
        transition: all 0.1s ease-out;
      }

      .checkbox-label input:checked ~ .checkbox-custom {
        background-color: white;
        border-radius: 50%;
        -webkit-transform: rotate(0deg) scale(1);
        -ms-transform: rotate(0deg) scale(1);
        transform: rotate(0deg) scale(1);
        opacity: 1;
        border: 2px solid white;
      }

      .checkbox-label input:checked ~ .checkbox-custom::after {
        -webkit-transform: rotate(45deg) scale(1);
        -ms-transform: rotate(45deg) scale(1);
        transform: rotate(45deg) scale(1);
        opacity: 1;
        left: 5px;
        top: -1px;
        width: 6px;
        height: 12px;
        border: solid #e6d374;
        border-width: 0 3px 3px 0;
        background-color: transparent;
        border-radius: 0;
      }

      button {
        word-break: keep-all;
        height: 25px;
        border: none;
        background-color: #e6d374;
        color: red;
        cursor: pointer;
      }
    }
  }
}
.checked {
  text-decoration-line: line-through;
  opacity: 0.5;
}
</style>
