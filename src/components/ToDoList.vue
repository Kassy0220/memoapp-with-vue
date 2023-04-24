<script>
import BaseButton from './BaseButton.vue'
import ToDoEditForm from './ToDoEditForm.vue'

export default {
  components: {
    BaseButton,
    ToDoEditForm
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
    updateToDo(formElement, id, content) {
      if (!content) {
        alert('ToDoの内容を入力してください')
        return
      }

      let updateForm = this.$el.querySelector(formElement)
      updateForm.submit()

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
  <div>
    <p>作成したToDo</p>
    <ul>
      <li
        v-for="todo in allTasks"
        :key="todo.id"
      >
        <template v-if="todo.isEditing">
          <ToDoEditForm
            :id="todo.id"
            v-model:content="todo.content"
            @updateToDo="updateToDo"
          ></ToDoEditForm>
        </template>

        <template v-else>
          {{ todo.content }}
          <div class="todo-buttons">
            <BaseButton @click="editToDo(todo.id)">編集</BaseButton>
            <BaseButton @click="deleteToDo(todo.id)">削除</BaseButton>
          </div>
        </template>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul {
  padding: 0;
}
li {
  padding: 0.5em;
  margin-bottom: 0.5em;
  border-left: 10px solid black;
  background-color: #eeeeee;
}
button {
  margin-right: 1em;
}
.todo-buttons {
  text-align: right;
}
</style>
