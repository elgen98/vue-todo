<template>
  <div>Total tasks: {{ counter }}</div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class TodoList extends Vue {
  @Prop() counter!: number;
}
</script>

<style lang="scss" scoped>
div {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  position: relative;
  left: 50%;
  color: #998a3d;
}
</style>
