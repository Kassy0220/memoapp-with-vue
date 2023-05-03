<script>
import BaseButton from './BaseButton.vue'
import ToDoUpdateForm from './ToDoUpdateForm.vue'

export default {
  components: {
    BaseButton,
    ToDoUpdateForm
  },
  props: {
    allToDos: Array
  },
  emits: ['deleteToDo', 'editToDo', 'updateToDo'],
  methods: {
    updateToDo(id, content) {
      this.$emit('updateToDo', id, content)
    }
  }
}
</script>

<template>
  <div>
    <p>作成したToDo</p>
    <ul>
      <li
        v-for="todo in allToDos"
        :key="todo.id"
      >
        <template v-if="todo.isEditing">
          <ToDoUpdateForm
            :id="todo.id"
            v-model:content="todo.content"
            @updateToDo="updateToDo"
          ></ToDoUpdateForm>
        </template>

        <template v-else>
          {{ todo.content }}
          <div class="todo-buttons">
            <BaseButton @click="$emit('editToDo', todo.id)">編集</BaseButton>
            <BaseButton @click="$emit('deleteToDo', todo.id)">削除</BaseButton>
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
  white-space: pre-wrap;
}
button {
  margin-right: 1em;
}
.todo-buttons {
  text-align: right;
}
</style>
