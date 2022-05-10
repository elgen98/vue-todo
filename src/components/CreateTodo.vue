<template>
  <div>
    <label for="todo">What's your next todo?</label>
    <input type="text" v-model="todoText" />
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script lang="ts">
import { Todo } from "../models/Todo";
import { Vue } from "vue-class-component";

export default class TodoList extends Vue {
  todoText = "";
  todoList = [];

  addTodo() {
    let newTodo: Todo = new Todo(this.todoText);
    this.todoList.push(newTodo);
    console.log(this.todoList);
  }
}
</script>

<style lang="scss" scoped></style>
