<template>
  <form action="" class="form-panel" v-if="showForm">
    <div class="form-section">
      <label for="item">Todo</label>
      <input type="text" class="form-input" />
    </div>

    <div class="form-section">
      <label for="date">Date</label>
      <input type="text" class="form-input" />
    </div>

    <div class="form-section">
      <label for="reminder">Reminder</label>
      <input type="checkbox" />
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
