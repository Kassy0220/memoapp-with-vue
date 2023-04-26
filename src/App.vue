<script>
import ToDoCreateForm from './components/ToDoCreateForm.vue'
import ToDoList from './components/ToDoList.vue'
import { v4 as uuidv4 } from 'uuid'

export default {
  components: {
    ToDoCreateForm,
    ToDoList
  },
  data() {
    return {
      allTasks: []
    }
  },
  methods: {
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoID = uuidv4()
      localStorage.setItem(todoID, content)
    }
  }
}
</script>

<template>
  <ToDoCreateForm @create="createToDo" />
  <ToDoList />
</template>
