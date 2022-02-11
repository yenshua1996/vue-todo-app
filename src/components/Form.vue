<template>
  <form class="form-panel" v-if="showForm" @submit="onSubmit">
    <div class="form-section">
      <label for="item">Todo</label>
      <input type="text" class="form-input" v-model="body" />
    </div>

    <div class="form-section">
      <label for="date">Date</label>
      <input type="text" class="form-input" v-model="date" />
    </div>

    <div class="form-section">
      <label for="reminder">Reminder</label>
      <input type="checkbox" v-model="reminder" />
    </div>

    <button class="btn btn-submit">Send</button>
  </form>

  <div class="placeholder-container" v-else>
    <h3>Start Adding</h3>
  </div>
</template>

<script>
export default {
  name: "Form",

  props: {
    showForm: {
      type: Boolean,
    },
  },

  data() {
    return {
      body: "",
      date: "",
      reminder: false,
    };
  },

  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.body) {
        alert("Please enter a valid todo!");
      }

      const todo = {
        body: this.body,
        date: this.date,
        reminder: this.reminder,
      };

      this.$emit("add-todo", todo);

      this.body = "";
      this.date = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.placeholder-container {
  text-align: center;
  padding: 2rem;
}

.form-panel {
  margin-bottom: 1rem;
}

.form-section {
  margin-bottom: 0.5rem;
}

label[for="reminder"] {
  margin-right: 0.5rem;
}

.btn-submit {
  display: block;
  width: 100%;
  background-color: rgb(28, 123, 255);
  color: #fff;
}
</style>
