<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      @delete-task="$emit('delete-task', task.id)"
      :tasks="tasks"
      :task="task"
      @toggleReminder="$emit('toggle-reminder', task.id)"
    />
  </div>
</template>
<script>
import Task from "./Task.vue"
export default {
  name: "Tasks",
  methods: {
    testing(id) {
      console.log(id)
    },
  },
  props: {
    tasks: Object,
  },
  components: {
    Task,
  },
  emits: ["delete-task", "toggle-reminder"],
}
</script>
<style>
.tasks {
  display: flex;
  flex-direction: column;
  gap: 1em;
}
</style>
