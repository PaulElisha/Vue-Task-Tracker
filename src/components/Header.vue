<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @toggle-Form="$emit('toggle-Form')"
      :text="showForm ? 'Close' : 'Add-Task'"
      :color="showForm ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  props: ["title", "showForm"],
  emits: ["toggle-Form"],
  components: {
    Button,
  },
  data() {
    return {
      toggleBtn: false,
    };
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: lighter;
}
</style>
