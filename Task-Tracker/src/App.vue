<template>
  <div class="container">

    <Header title="Task Tracker" @btn-click="toggleAddTask"/>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    <!-- tasks automatically calls data -->
    <Tasks :tasks="tasks" @toggle-reminder="toggleReminder" @delete-task="deleteTask"/>
    <router-view></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';
import { toHandlers } from 'vue';
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
    Footer
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    deleteTask(id) {
      console.log(id);
      this.tasks = this.tasks.filter((task) => task.id != id);
    },
    addTask(task) {
      this.tasks.push(task);
    },
    toggleReminder(id) {
      console.log(id);
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task);
    },
    toggleAddTask() {
      console.log('toggle');
      this.showAddTask = !this.showAddTask;
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "task 1",
        day: 'March 1st at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: "task 2",
        day: 'March 1st at 2:30pm',
        reminder: true
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
