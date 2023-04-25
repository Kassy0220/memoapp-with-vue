<script>
import BaseButton from './BaseButton.vue'
import { v4 as uuidv4 } from 'uuid'

export default {
  components: {
    BaseButton
  },
  data() {
    return {
      todoContent: ''
    }
  },
  methods: {
    createToDo() {
      if (!this.todoContent) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoID = uuidv4()
      localStorage.setItem(todoID, this.todoContent)
    }
  }
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
      <BaseButton @click="createToDo">新規作成</BaseButton>
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
