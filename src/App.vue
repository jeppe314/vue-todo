<template>
  <div class="container">
    <Header />
    <AddTask />
    <Tasks />
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue"
import Header from "./components/Header"
import Tasks from "./components/Tasks.vue"
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
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
