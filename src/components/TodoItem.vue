<template>
  <article :class="[todo.reminder ? 'reminder' : '', 'todo-item']">
    <div class="content-container" @dblclick="$emit('toggle-reminder')">
      <div v-if="toggleUpdateForm">
        <form @submit.prevent="() => onSubmit(todo.id)">
          <input type="text" v-model="updateBodyForm" />
        </form>
      </div>

      <div v-else>
        <div class="content-text">
          <h5>{{ todo.body }}</h5>
          <p>{{ todo.date }}</p>
        </div>
      </div>

      <div class="utility">
        <i class="fas fa-trash" @click="$emit('delete-todo')"></i>
        <i class="fas fa-pen" @click="editTodo"></i>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: "TodoItem",

  data() {
    return {
      toggleUpdateForm: false,
      updateBodyForm: "",
    };
  },

  props: {
    todo: {
      type: Object,
    },
  },

  methods: {
    editTodo(e) {
      e.preventDefault();
      this.toggleUpdateForm = !this.toggleUpdateForm;
    },

    onSubmit(id) {
      this.$parent.$emit("update-todo", { payload: this.updateBodyForm, id });
      this.updateBodyForm = "";
      this.toggleUpdateForm = !this.toggleUpdateForm;
    },
  },
};
</script>

<style scoped>
h5 {
  font-weight: 500;
  margin-bottom: 0.5rem;
  font-size: 1.35rem;
}

.todo-item {
  background-color: rgb(241, 241, 241);
  padding: 1rem;
  margin-bottom: 0.5rem;
  border-left: 10px solid rgb(241, 241, 241);
  border-radius: 2px;
}

.content-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.utility {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.content-container:hover {
  cursor: pointer;
}

.fas {
  color: rgb(25, 25, 25);
  transition: transform 200ms linear, color 200ms linear;
}

.fas:hover {
  transform: translateY(-2px);
  color: rgb(167, 167, 167);
  cursor: pointer;
}

.reminder {
  border-left: 10px solid rgb(11, 211, 0);
}
</style>
