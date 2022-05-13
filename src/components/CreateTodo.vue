<template>
  <section>
    <label for="todo">What's your next todo?</label>
    <div>
      <input type="text" v-model="userInput" @keypress.enter="addTodo" />
      <button @click="addTodo">Add</button>
    </div>
  </section>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class TodoList extends Vue {
  userInput = "";
  errorMsg = "";

  addTodo() {
    if (this.userInput.length > 0) {
      this.$emit("sendTodo", this.userInput);
      this.userInput = "";
    } else alert("Input is empty!");
  }
}
</script>

<style lang="scss" scoped>
label {
  font-family: "Lucida Sans";
}
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  div {
    max-width: 177px;

    button {
      cursor: pointer;
      width: 15%;
      position: relative;
      left: 80%;
      border: none;
      background-color: white;
    }
  }
}
</style>
