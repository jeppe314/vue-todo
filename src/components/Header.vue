<template>
  <div class="header">
    <div class="nav">
      <h1>Todo-list</h1>
      <Button @btn-click="$emit('toggle-add-task')" title="Add task" />
    </div>
    <div class="footer">
      <AddTask v-show="showAddTask" />
    </div>
  </div>
</template>
<script>
import Button from "./Button.vue"
import AddTask from "./AddTask.vue"
export default {
  name: "Header",
  components: {
    Button,
    AddTask,
  },
  props: {
    showAddTask: Boolean,
  },
}
</script>
<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}

.nav {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-bottom: 1em;
}
.footer {
  width: 100%;
}
</style>
