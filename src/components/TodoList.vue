<template>
  <section class="todo-list">
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem
        :todo="todo"
        @toggle-reminder="$emit('toggle-reminder', todo.id)"
        @delete-todo="$emit('delete-todo', todo.id)"
        @update-todo="$emit('update-todo')"
      />
    </div>
  </section>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",

  props: {
    todos: {
      type: Array,
    },
  },

  components: {
    TodoItem,
  },
};
</script>

<style scoped></style>
