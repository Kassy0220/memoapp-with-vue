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
  mounted() {
    if (localStorage.length > 0) {
      this.allTasks = this.parseTasks()
    }
  },
  methods: {
    parseTasks() {
      let allTasks = Object.entries(localStorage).map((record) => {
        let todo = {}
        todo.id = record[0]
        todo.content = record[1]
        todo.isEditing = false
        return todo
      })
      return allTasks.sort((a, b) => a.id - b.id)
    },
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoID = uuidv4()
      localStorage.setItem(todoID, content)
    },
    deleteToDo(id) {
      this.allTasks = this.allTasks.filter((todo) => !(todo.id === id))
      localStorage.removeItem(id)
    },
    editToDo(id) {
      if (this.allTasks.find((todo) => todo.isEditing)) {
        alert('既に編集中のToDOがあります')
        return
      }

      for (const todo of this.allTasks) {
        if (todo.id === id) {
          todo.isEditing = true
        }
      }
    },
    updateToDo(id, content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      for (const todo of this.allTasks) {
        if (todo.id === id) {
          todo.content = content
          todo.isEditing = false
        }
      }
      localStorage.setItem(id, content)
    }
  }
}
</script>

<template>
  <ToDoCreateForm @create="createToDo" />
  <ToDoList
    :allTasks="allTasks"
    v-on="{
      delete: this.deleteToDo,
      edit: this.editToDo,
      update: this.updateToDo
    }"
  />
</template>
