<template>
  <div>
    <button @click="onClick" :style="{ background: color }" class="btn">
      {{ text }}
    </button>
  </div>
</template>

<script>
export default {
  props: ["text", "color"],
  methods: {
    onClick() {
      this.$emit("toggle-form");
    },
  },
};
</script>

<style scoped>
.btn {
  border: none;
  outline: none;
  color: white;
  font-size: 14px;
  padding: 10px;
  border-radius: 4px;
  cursor: pointer;
}
</style>
