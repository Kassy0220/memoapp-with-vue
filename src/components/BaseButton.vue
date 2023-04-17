<script>
export default {
  emits: ['click']
}
</script>

<template>
  <button @click="$emit('click')"><slot></slot></button>
</template>
