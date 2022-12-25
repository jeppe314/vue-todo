<template>
  <div class="container">
    <Header
      @toggle-add-task="toggleAddTask"
      :showAddTask="this.showAddTask"
      @add-task="postTask"
    />
    <Tasks
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script>
import Header from "./components/Header"
import Tasks from "./components/Tasks.vue"
export default {
  name: "App",
  data() {
    return {
      showAddTask: true,
      tasks: {},
    }
  },
  methods: {
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updatedTask = { ...taskToToggle, reminder: !taskToToggle.reminder }
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(updatedTask),
      })

      const data = await res.json()

      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      )
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    async postTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          text: task.text,
          time: task.time,
          reminder: task.reminder,
        }),
      })
      const data = await res.json()
      this.tasks = [...this.tasks, data]
    },
    async deleteTask(id) {
      const res = await fetch(`api/tasks/${id}`, {
        method: "DELETE",
      })

      this.tasks = this.tasks.filter((task) => task.id != id)
    },
    async fetchTasks() {
      const res = await fetch("api/tasks")
      const data = res.json()
      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)
      const data = res.json()
      return data
    },
  },
  async created() {
    this.tasks = await this.fetchTasks()
  },
  components: {
    Header,
    Tasks,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100vw;
  height: 100vh;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  width: 500px;
  border: 2px dashed rgb(79, 75, 75);
  margin: 30px auto;
  display: flex;
  flex-direction: column;
  gap: 1em;
  padding: 1em;
}
</style>
