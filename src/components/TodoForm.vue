<template>
  <form @submit.prevent="form" class="mb-4">
    <input
      type="text"
      class="form-control form-control-lg my-3"
      placeholder="Enter to do"
      v-model.trim="text"
    />
    <button class="btn btn-dark btn-lg w-100 fw-bold">Create</button>
  </form>
</template>

<script>
import { inject, ref } from "@vue/runtime-core";

export default {
  setup() {
    const todos = inject("todos");
    const text = ref("");

    const form = () => {
      const textValue = text.value;
      if (textValue === "") {
        console.log("Esta vació");
        return;
      }

      const todo = {
        text: textValue,
        state: false,
        id: Date.now(),
      };

      todos.value.push(todo);
      text.value = "";
    };
    return { form, text };
  },
};
</script>

<style></style>
