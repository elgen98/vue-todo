<template>
  <div>
    <label for="todo">What's your next todo?</label>
    <input type="text" v-model="userInput" />
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class TodoList extends Vue {
  userInput = "";

  addTodo() {
    if (this.userInput.length > 0) {
      this.$emit("sendTodo", this.userInput);
      this.userInput = "";
    } else alert("Input is empty!");
  }
}
</script>

<style lang="scss" scoped></style>
