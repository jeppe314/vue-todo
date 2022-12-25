<template>
  <div class="addtask">
    <div>
      <label for="text">Task</label>
      <input type="text" name="text" placeholder="Add task" v-model="text" />
    </div>
    <div>
      <label for="time">Time</label>
      <input
        type="text"
        name="time"
        placeholder="Add time &  day"
        v-model="time"
      />
    </div>
    <div class="reminder">
      <label for="reminder">Set reminder</label>
      <input type="checkbox" v-model="reminder" />
    </div>
    <Button title="Submit" @click="onSubmit" />
  </div>
</template>
<script>
import Button from "./Button.vue"
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      time: "",
      reminder: false,
    }
  },
  components: {
    Button,
  },
  methods: {
    resetForm() {
      this.text = ""
      this.time = ""
      this.reminder = false
    },
    async onSubmit() {
      if (this.text && this.time) {
        const newTask = {
          text: this.text,
          time: this.time,
          reminder: this.reminder,
        }
        this.$emit("add-task", newTask)
        this.resetForm()
      }
    },
  },
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
.reminder {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
