<script>
export default {
  data() {
    return {
      allMemos: this.parseMemos()
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
      </li>
    </ul>
  </div>
</template>
