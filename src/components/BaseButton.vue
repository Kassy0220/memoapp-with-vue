<script>
export default {
  emits: ['click']
}
</script>

<template>
  <button @click="$emit('click')"><slot></slot></button>
</template>

<style scoped>
button {
  padding: 0.2em 0.5em 0.2em 0.5em;
  border: solid 1px #555555;
  border-radius: 3px;
}
button:hover {
  color: white;
  background-color: #555555;
}
</style>
