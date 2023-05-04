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
      allToDos: []
    }
  },
  mounted() {
    const allToDos = JSON.parse(localStorage.getItem('allToDos'))
    if (allToDos !== null) {
      this.allToDos = allToDos
    }
  },
  methods: {
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todo = { id: uuidv4(), content, isEditing: false }
      this.allToDos.push(todo)
      this.saveToDo()
    },
    deleteToDo(id) {
      this.allToDos = this.allToDos.filter((todo) => todo.id !== id)
      this.saveToDo()
    },
    editToDo(id) {
      if (this.allToDos.some((todo) => todo.isEditing)) {
        alert('既に編集中のToDoがあります')
        return
      }

      const todoInEdit = this.allToDos.find((todo) => todo.id === id)
      todoInEdit.isEditing = true
      this.saveToDo()
    },
    updateToDo(id, content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoInUpdate = this.allToDos.find((todo) => todo.id === id)
      todoInUpdate.content = content
      todoInUpdate.isEditing = false
      this.saveToDo()
    },
    saveToDo() {
      localStorage.setItem('allToDos', JSON.stringify(this.allToDos))
    }
  }
}
</script>

<template>
  <ToDoCreateForm @createToDo="createToDo" />
  <ToDoList
    :allToDos="allToDos"
    @deleteToDo="deleteToDo"
    @editToDo="editToDo"
    @updateToDo="updateToDo"
  />
</template>
