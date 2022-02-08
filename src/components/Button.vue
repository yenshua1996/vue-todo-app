<template>
  <button
    :class="[showForm ? addTask : backToStart, 'btn']"
    @click="$emit('btn-click')"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",

  data() {
    return {
      addTask: "add",
      backToStart: "back",
    };
  },

  props: {
    text: {
      type: String,
    },
    showForm: {
      type: Boolean,
    },
  },
};
</script>

<style scoped>
.add {
  background-color: rgb(0, 189, 44);
  color: #fff;
}

.back {
  background-color: rgb(12, 162, 255);
  color: #fff;
}
</style>
