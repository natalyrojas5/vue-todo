<template>
  <li class="list-group-item d-flex align-items-center justify-content-between">
    <span
      role="button"
      class="fs-5"
      @click="completed(todo.id)"
      :class="{ tachado: todo.state }"
      >{{ todo.text }}</span
    >
    <span role="button" @click="deleteTodo(todo.id)"
      ><i class="fas fa-times"></i
    ></span>
  </li>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  setup() {
    const todos = inject("todos");
    const deleteTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    const completed = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) {
          todo.state = true;
        }
        return todo;
      });
    };
    return { completed, deleteTodo };
  },
};
</script>

<style>
.tachado {
  text-decoration: line-through;
}
</style>
