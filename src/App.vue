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
      this.allTasks = JSON.parse(localStorage.getItem('allTasks'))
    }
  },
  methods: {
    createToDo(content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      const todo = { id: uuidv4(), content: content, isEditing: false }
      this.allTasks.push(todo)
      this.saveTask()
    },
    deleteToDo(id) {
      this.allTasks = this.allTasks.filter((todo) => !(todo.id === id))
      this.saveTask()
    },
    editToDo(id) {
      if (this.allTasks.find((todo) => todo.isEditing)) {
        alert('既に編集中のToDoがあります')
        return
      }

      for (const todo of this.allTasks) {
        if (todo.id === id) {
          todo.isEditing = true
        }
      }
      this.saveTask()
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
      this.saveTask()
    },
    saveTask() {
      localStorage.setItem('allTasks', JSON.stringify(this.allTasks))
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
