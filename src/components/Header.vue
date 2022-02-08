<template>
  <header>
    <h1>Todo App</h1>

    <Button
      :text="showForm ? 'Back' : 'Add Task'"
      :showForm="showForm"
      @btn-click="$emit('btn-click')"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "Header",

  components: {
    Button,
  },

  props: {
    showForm: {
      type: Boolean,
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}
</style>
