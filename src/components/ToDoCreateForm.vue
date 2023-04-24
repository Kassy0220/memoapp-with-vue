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
  methods: {
    saveToDo() {
      if (!this.todoContent) {
        alert('ToDoの内容を入力してください')
        return
      }

      let todoID = this.assignToDoID()
      localStorage.setItem(todoID, this.todoContent)
    },
    assignToDoID() {
      if (localStorage.length === 0) {
        return 1
      }

      let maxToDoID = Object.keys(localStorage)
        .map((id) => Number(id))
        .reduce((a, b) => Math.max(a, b))
      return maxToDoID + 1
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
      <BaseButton @click="saveToDo">新規作成</BaseButton>
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
