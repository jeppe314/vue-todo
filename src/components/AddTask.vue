<template>
  <div class="addtask">
    <div>
      <label for="text">Task</label>
      <input type="text" name="text" placeholder="Add task" />
    </div>
    <div>
      <label for="time">Time</label>
      <input type="text" name="time" placeholder="Add time &  day" />
    </div>
  </div>
</template>
<script>
export default {
  name: "AddTask",
}
</script>
<style scoped>
.addtask {
  display: flex;
  flex-direction: column;
  gap: 1em;
}
label {
  display: block;
  font-family: Verdana;
  margin-bottom: 0.3em;
}
input {
  width: 100%;
  padding: 1em 0.5em;
}
</style>
