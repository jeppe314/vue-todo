<template>
  <div class="task">
    <div>
      <h3>{{ task.text }}</h3>
      <p>{{ task.time }}</p>
    </div>
    <i class="fa-solid fa-xmark"></i>
  </div>
</template>
<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
}
</script>
<style>
.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgba(198, 197, 144, 0.11);
  padding: 1em;
}

h3 {
  margin-bottom: 0.5em;
}

.fa-xmark {
  color: rgb(205, 85, 85);
  font-size: 1.5em;
}
</style>
