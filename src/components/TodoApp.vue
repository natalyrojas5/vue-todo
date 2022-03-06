<template>
  <div class="app-main bg-warning d-flex align-items-center">
    <div class="container p-4 p-lg-0">
      <div class="row">
        <div class="col-lg-6 rounded bg-white m-auto p-5">
          <h1 class="fw-bold text-center fs-1">TO DO APP</h1>
          <todo-form />
          <todo-list />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { provide, ref, watchEffect } from "vue";
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";
export default {
  components: { TodoForm, TodoList },

  setup() {
    const todos = ref([]);
    provide("todos", todos);

    if (localStorage.getItem("todos")) {
      todos.value = JSON.parse(localStorage.getItem("todos"));
    }

    watchEffect(() => {
      localStorage.setItem("todos", JSON.stringify(todos.value));
    });
  },
};
</script>

<style>
.app-main {
  min-height: 100vh;
}
</style>
