<template>
  <div class="tasks">
    <div :key="task.id" v-for="task in tasks">
      <Task :task="task" />
    </div>
  </div>
</template>
<script>
import Task from "./Task.vue"
export default {
  name: "Tasks",
  data() {
    return {
      tasks: [
        { id: 1, text: "Go to gym", time: "March 3 15pm", reminder: false },
        { id: 2, text: "Buy groceries", time: "Feb 15pm", reminder: true },
        { id: 3, text: "Clean clothes", time: "Dec 3 15pm", reminder: false },
      ],
    }
  },
  components: {
    Task,
  },
}
</script>
<style>
.tasks {
  display: flex;
  flex-direction: column;
  gap: 1em;
}
</style>
