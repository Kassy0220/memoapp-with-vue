<script>
import BaseButton from './BaseButton.vue'

export default {
  components: {
    BaseButton
  },
  props: {
    id: String,
    content: String
  },
  emits: ['update:content', 'updateMemo']
}
</script>

<template>
  <div>
    <form id="update-form">
      <textarea
        :value="content"
        @input="$emit('update:content', $event.target.value)"
      />
      <BaseButton @click="$emit('updateMemo', '#update-form', id, content)">更新</BaseButton>
    </form>
  </div>
</template>
