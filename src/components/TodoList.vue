<template>
  <ul class="list-group">
    <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" />
    <todo-empty />
  </ul>
  <todo-footer v-if="todos.length !== 0" />
  <todo-filter />
</template>

<script>
import { computed, inject, provide, ref } from "@vue/runtime-core";
import TodoItem from "./TodoItem.vue";
import TodoFooter from "./TodoFooter.vue";
import TodoEmpty from "./TodoEmpty.vue";
import TodoFilter from "./TodoFilter.vue";
export default {
  components: { TodoItem, TodoFooter, TodoEmpty, TodoFilter },
  setup() {
    const listaTodos = inject("todos");

    const state = ref("all");

    const todos = computed(() => {
      if (state.value === "all") return listaTodos.value;
      if (state.value === "active")
        return listaTodos.value.filter((todo) => !todo.state);
      if (state.value === "complete")
        return listaTodos.value.filter((todo) => todo.state);
    });

    provide("state", state);

    return { todos };
  },
};
</script>

<style></style>
