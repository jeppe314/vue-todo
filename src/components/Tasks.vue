<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      @delete-task="$emit('delete-task', task.id)"
      :tasks="tasks"
      :task="task"
    />
  </div>
</template>
<script>
import Task from "./Task.vue"
export default {
  name: "Tasks",
  props: {
    tasks: Object,
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
