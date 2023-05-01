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
    // 一度もToDoを作成していない場合 allTasks は null になる
    const allTasks = JSON.parse(localStorage.getItem('allTasks'))
    this.allTasks = allTasks || []
  },
  methods: {
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todo = { id: uuidv4(), content, isEditing: false }
      this.allTasks.push(todo)
      this.saveTask()
    },
    deleteToDo(id) {
      this.allTasks = this.allTasks.filter((todo) => todo.id !== id)
      this.saveTask()
    },
    editToDo(id) {
      if (this.allTasks.some((todo) => todo.isEditing)) {
        alert('既に編集中のToDoがあります')
        return
      }

      const todoInEdit = this.allTasks.find((todo) => todo.id === id)
      todoInEdit.isEditing = true
      this.saveTask()
    },
    updateToDo(id, content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todoInUpdate = this.allTasks.find((todo) => todo.id === id)
      todoInUpdate.content = content
      todoInUpdate.isEditing = false
      this.saveTask()
    },
    saveTask() {
      localStorage.setItem('allTasks', JSON.stringify(this.allTasks))
    }
  }
}
</script>

<template>
  <ToDoCreateForm @createToDo="createToDo" />
  <ToDoList
    :allTasks="allTasks"
    @deleteToDo="this.deleteToDo"
    @editToDo="this.editToDo"
    @updateToDo="this.updateToDo"
  />
</template>
