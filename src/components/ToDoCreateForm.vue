<script>
import BaseButton from './BaseButton.vue'

export default {
  components: {
    BaseButton
  },
  data() {
    return {
      todoContent: ''
    }
  },
  emits: ['create']
}
</script>

<template>
  <div>
    <form id="create-form">
      <label for="todo-content">ToDoを作成 :</label>
      <textarea
        v-model="todoContent"
        id="todo-content"
        placeholder="ToDoの内容を入力"
      />
      <BaseButton @click="$emit('create', todoContent)">新規作成</BaseButton>
    </form>
  </div>
</template>

<style scoped>
label {
  vertical-align: middle;
  margin-right: 1em;
}
#todo-content {
  width: 200px;
  height: 100px;
  vertical-align: middle;
  margin-right: 1em;
}
</style>
