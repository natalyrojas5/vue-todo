<template>
  <li
    v-if="todos.length === 0"
    class="list-group-item bg-danger text-white p-3"
  >
    <p class="m-0 fw-bold fs-5">No results found</p>
  </li>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  setup() {
    const todos = inject("todos");
    return { todos };
  },
};
</script>

<style></style>
