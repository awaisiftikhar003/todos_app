<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div class="container">
    <Header title="Task Tracker" :flag="showAddTask" @add-task="addTask" />
    <TaskForm v-show="showAddTask" @save-task="saveTask" />
    <Tasks
      @delete-task="deleteTask"
      @toggle-status="togglestatus"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import TaskForm from "./components/TaskForm.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    TaskForm,
  },
  data() {
    return { tasks: [], showAddTask: false };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Task 1",
        desc: "This is a demo task",
        status: true,
      },
      {
        id: 2,
        text: "Task 2",
        desc: "This is description of second task",
        status: false,
      },
      {
        id: 3,
        text: "Task 3",
        desc: "Third demo task",
        status: false,
      },
    ];
    this.showAddTask = false;
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are yuou sure?")) {
        this.tasks = this.tasks.filter((task) => {
          return task.id != id;
        });
      }
    },
    togglestatus(id) {
      this.tasks.map((task) => {
        if (task.id == id) {
          task.status = !task.status;
        }
      });
    },
    addTask() {
      this.showAddTask = !this.showAddTask;
    },
    saveTask(newTask) {
      this.tasks.push(newTask);
      this.showAddTask = false;
      alert("Task saved!");
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
