<template>
  <button @click="handleClick" class="btn">{{ title }}</button>
</template>
<script>
export default {
  name: "Button",
  props: {
    title: String,
  },
  methods: {
    handleClick() {
      this.$emit("btn-click")
    },
  },
}
</script>
<style>
.btn {
  color: white;
  background: black;
  border-radius: 5px;
  border: none;
  padding: 1em;
  cursor: pointer;
}
</style>
