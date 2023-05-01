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
      allToDoes: []
    }
  },
  mounted() {
    const allToDoes = JSON.parse(localStorage.getItem('allToDoes'))
    if (allToDoes !== null) {
      this.allToDoes = allToDoes
    }
  },
  methods: {
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todo = { id: uuidv4(), content, isEditing: false }
      this.allToDoes.push(todo)
      this.saveToDo()
    },
    deleteToDo(id) {
      this.allToDoes = this.allToDoes.filter((todo) => todo.id !== id)
      this.saveToDo()
    },
    editToDo(id) {
      if (this.allToDoes.some((todo) => todo.isEditing)) {
        alert('既に編集中のToDoがあります')
        return
      }

      const todoInEdit = this.allToDoes.find((todo) => todo.id === id)
      todoInEdit.isEditing = true
      this.saveToDo()
    },
    updateToDo(id, content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoInUpdate = this.allToDoes.find((todo) => todo.id === id)
      todoInUpdate.content = content
      todoInUpdate.isEditing = false
      this.saveToDo()
    },
    saveToDo() {
      localStorage.setItem('allToDoes', JSON.stringify(this.allToDoes))
    }
  }
}
</script>

<template>
  <ToDoCreateForm @createToDo="createToDo" />
  <ToDoList
    :allToDoes="allToDoes"
    @deleteToDo="deleteToDo"
    @editToDo="editToDo"
    @updateToDo="updateToDo"
  />
</template>
