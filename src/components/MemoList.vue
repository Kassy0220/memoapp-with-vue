<script>
import BaseButton from './BaseButton.vue'

export default {
  components: {
    BaseButton
  },
  data() {
    return {
      allMemos: []
    }
  },
  mounted() {
    if (localStorage.length > 0) {
      this.allMemos = this.parseMemos()
    }
  },
  methods: {
    parseMemos() {
      let memos = Object.entries(localStorage).map((record) => {
        let memo = {}
        memo.id = record[0]
        memo.content = record[1]
        memo.isEditing = false
        return memo
      })
      return memos.sort((a, b) => a.id - b.id)
    },
    deleteMemo(id) {
      this.allMemos = this.allMemos.filter((memo) => !(memo.id === id))
      localStorage.removeItem(id)
    }
  }
}
</script>

<template>
  <div>
    <p>作成したメモ</p>
    <ul>
      <li
        v-for="memo in allMemos"
        :key="memo.id"
      >
        {{ memo.content }}
        <BaseButton @click="deleteMemo(memo.id)">削除</BaseButton>
      </li>
    </ul>
  </div>
</template>
