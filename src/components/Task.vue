<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="['task', task.reminder ? 'reminder' : '']"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  emits: ["delete-task", "toggle-reminder"],
  data() {
    return {};
  },
};
</script>

<style scoped>
div {
  cursor: pointer;
  user-select: none;
}
.task {
  width: 100%;
  padding: 10px;
  border-radius: 4px;
  background-color: rgba(128, 128, 128, 0.205);
  margin: 5px 0;
  font-weight: lighter;
}

h3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.fas {
  color: red;
  cursor: pointer;
}

.reminder {
  border-left: 4px solid green;
}
</style>
