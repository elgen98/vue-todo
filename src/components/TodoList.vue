<template>
  <div>
    <CreateTodo @sendTodo="getTodo($event)"></CreateTodo>
    <ul v-for="(todo, i) in todoArray" :key="i">
      <li :class="todo.done ? 'checked' : 'unchecked'">
        {{ todo.text }}
      </li>
      <input type="checkbox" @click="checkTodo(i)" />
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

  checkTodo(itemIndex: number) {
    this.todoArray[itemIndex].done = true;
  }
}
</script>

<style lang="scss" scoped>
.checked {
  text-decoration-line: line-through;
  opacity: 0.5;
}
</style>
