<template>
  <div class="header">
    <h1>Todo-list</h1>
    <Button />
  </div>
</template>
<script>
import Button from "./Button.vue"
export default {
  name: "Header",
  components: {
    Button,
  },
}
</script>
<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
