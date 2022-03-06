<template>
  <li
    class="
      list-group-item
      d-flex
      justify-content-between
      bg-dark
      text-warning
      fw-bold
    "
  >
    <span role="button">{{ counterCompleted }} Activated</span>
    <span role="button" @click="deleteCompleted">Delete completed</span>
  </li>
</template>

<script>
import { computed, inject } from "@vue/runtime-core";
export default {
  setup() {
    const todos = inject("todos");

    const counterCompleted = computed(() => {
      return todos.value.filter((todo) => !todo.state).length;
    });

    const deleteCompleted = () => {
      todos.value = todos.value.filter((todo) => !todo.state);
    };

    return { counterCompleted, deleteCompleted };
  },
};
</script>

<style></style>
