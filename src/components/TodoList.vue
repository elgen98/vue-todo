<template>
  <div>
    <CreateTodo @sendTodo="handleTodo($event)"></CreateTodo>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import CreateTodo from "./CreateTodo.vue";
@Options({
  components: {
    CreateTodo,
  },
})
export default class TodoList extends Vue {
  handleTodo(t: object) {
    console.log("Emit successful", t);
  }
}
</script>

<style lang="scss" scoped></style>
