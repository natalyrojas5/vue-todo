<template>
  <div class="card mt-3">
    <div class="todo-filter card-body text-dark p-0 text-center bg-warning">
      <span
        role="button"
        class="fw-bold fs-5 p-3 d-block"
        :class="state === 'active' ? 'bg-dark text-white' : 'bg-warning'"
        @click="filter('active')"
        >Active
      </span>
      <span
        role="button"
        class="fw-bold fs-5 p-3 d-block"
        :class="state === 'all' ? 'bg-dark text-white' : 'bg-warning'"
        @click="filter('all')"
        >All</span
      >
      <span
        role="button"
        class="fw-bold fs-5 p-3 d-block"
        :class="state === 'complete' ? 'bg-dark text-white' : 'bg-warning'"
        @click="filter('complete')"
        >Complete</span
      >
    </div>
  </div>
</template>

<script>
import { inject } from "@vue/runtime-core";
export default {
  setup() {
    const state = inject("state");
    const filter = (value) => (state.value = value);
    return { filter, state };
  },
};
</script>

<style scoped>
.todo-filter {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  align-items: center;
  justify-content: center;
}
@media screen and (max-width: 768px) {
  .todo-filter {
    grid-template-columns: 1fr;
  }
}
</style>
