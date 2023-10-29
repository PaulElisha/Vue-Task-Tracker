<template>
  <div class="app">
    <Header
      @toggle-Form="toggleForm"
      :showForm="showForm"
      title="Task Tracker"
    />
    <div v-show="showForm">
      <AddTask @add-task="AddTask" />
    </div>
    <TaskList
      @toggle-reminder="toggleReminder"
      @delete-task="delTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import TaskList from "./components/TaskList.vue";
import AddTask from "./components/AddTask.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    AddTask,
    TaskList,
  },
  data() {
    return {
      tasks: [],
      showForm: false,
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
    },
    AddTask() {
      this.tasks = [...this.tasks, data];
    },
    delTask(id) {
      console.log("task", id);
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id == id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: "1",
        text: "Doctors Appointment",
        day: "March 5th at 2:30pm",
        reminder: true,
      },
      {
        id: "2",
        text: "Meeting with boss",
        day: "March 6th at 1:30pm",
        reminder: true,
      },
      {
        id: "3",
        text: "Food shopping",
        day: "March 7th at 2:00pm",
        reminder: false,
      },
      {
        text: "Go to gym",
        day: " Sunday at 10 am",
        reminder: true,
        id: "8n1MLb2",
      },
    ];
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}

.app {
  border: 1px solid black;
  width: 450px;
  margin: auto;
  margin-top: 40px;
  border-radius: 4px;
  padding: 25px;
}
</style>
