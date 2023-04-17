<script>
import BaseButton from './BaseButton.vue'

export default {
  components: {
    BaseButton
  },
  data() {
    return {
      memoContent: ''
    }
  },
  methods: {
    saveMemo() {
      if (!this.memoContent) {
        alert('メモの内容を入力してください')
        return
      }

      let memoID = this.assignMemoID()
      localStorage.setItem(memoID, this.memoContent)
    },
    assignMemoID() {
      if (localStorage.length === 0) {
        return 1
      }

      let maxMemoID = Object.keys(localStorage)
        .map((id) => Number(id))
        .reduce((a, b) => Math.max(a, b))
      return maxMemoID + 1
    }
  }
}
</script>

<template>
  <div>
    <form id="create-form">
      <label for="memo-content">メモの作成 :</label>
      <textarea
        v-model="memoContent"
        id="memo-content"
        placeholder="メモ内容を入力"
      />
      <BaseButton @click="saveMemo">新規作成</BaseButton>
    </form>
  </div>
</template>
