<script>
import BaseButton from './BaseButton.vue'

export default {
  components: {
    BaseButton
  },
  props: {
    id: String,
    content: String
  },
  emits: ['update:content', 'updateToDo']
}
</script>

<template>
  <div>
    <form id="update-form">
      <textarea
        :value="content"
        @input="$emit('update:content', $event.target.value)"
      />
      <BaseButton @click="$emit('updateToDo', id, content)">更新</BaseButton>
    </form>
  </div>
</template>

<style scoped>
textarea {
  width: 200px;
  height: 100px;
  margin-right: 1em;
  vertical-align: middle;
}
</style>
