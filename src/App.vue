<script>
import ToDoCreateForm from './components/ToDoCreateForm.vue'
import ToDoList from './components/ToDoList.vue'

export default {
  components: {
    ToDoCreateForm,
    ToDoList
  }
}
</script>

<template>
  <ToDoCreateForm />
  <ToDoList />
</template>
