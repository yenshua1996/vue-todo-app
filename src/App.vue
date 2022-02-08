<template>
  <div class="container">
    <div class="app-container">
      <Header @btn-click="toggleForm" :showForm="showForm" />
      <Form :showForm="showForm" />
      <TodoList
        :todos="todos"
        @toggle-reminder="toggleReminder"
        @delete-todo="deleteTodo"
        @update-todo="updateTodo"
      />
    </div>
  </div>
</template>

<script>
//import components
import Header from "./components/Header.vue";
import TodoList from "./components/TodoList.vue";
import Form from "./components/Form.vue";

export default {
  //register component
  components: {
    Header,
    TodoList,
    Form,
  },

  //State
  data() {
    return {
      showForm: false,
      todos: [],
    };
  },

  //register custom events
  emits: ["btn-click", "toggle-reminder", "delete-todo", "update-todo"],

  //component methods
  methods: {
    // toggle form input
    toggleForm() {
      this.showForm = !this.showForm;

      console.log(this.showForm);
    },

    // toggle reminder
    toggleReminder(id) {
      this.todos = this.todos.map((todo) =>
        todo.id === id ? { ...todo, reminder: !todo.reminder } : todo
      );
    },

    // delete todo item
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },

    // update todo item
    updateTodo(input) {
      this.todos = this.todos.map((todo) =>
        todo.id === input.id ? { ...todo, body: input.payload } : todo
      );
    },
  },

  //Lifecycle methods
  created() {
    this.todos = [
      {
        id: 1,
        body: "Doing Something",
        date: "Feb 15th at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        body: "Something is going on",
        date: "Feb 15th at 2:30pm",
        reminder: false,
      },
      {
        id: 3,
        body: "Starting my assignment",
        date: "Feb 15th at 2:30pm",
        reminder: true,
      },
      {
        id: 4,
        body: "Finish my assignment",
        date: "Feb 15th at 2:30pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap");

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: "Poppins", sans-serif;
  line-height: 1.6;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

h1,
h2,
h3 {
  font-weight: 400;
}

.container {
  width: 50%;
  margin: 0 auto;
}

.app-container {
  border: 1px solid rgb(220, 218, 218);
  padding: 1rem;
  border-radius: 2px;
}

input[type="text"] {
  display: block;
  width: 100%;
  font-size: 1.25rem;
  padding: 0.5rem;
}

.btn {
  display: inline-block;
  border: none;
  border-radius: 2px;
  padding: 0.5rem 1rem;
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  transition: background 200ms linear, color 200ms linear;
}

.btn:hover {
  cursor: pointer;
  outline: none;
}
</style>
