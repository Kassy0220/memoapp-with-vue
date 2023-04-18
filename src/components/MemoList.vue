<script>
import BaseButton from './BaseButton.vue'
import MemoEditForm from './MemoEditForm.vue'

export default {
  components: {
    BaseButton,
    MemoEditForm
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
    },
    editMemo(id) {
      if (this.allMemos.find((memo) => memo.isEditing)) {
        alert('既に編集中のメモがあります')
        return
      }

      for (const memo of this.allMemos) {
        if (memo.id === id) {
          memo.isEditing = true
        }
      }
    },
    updateMemo(formElement, id, content) {
      if (!content) {
        alert('メモの内容を入力してください')
        return
      }

      let updateForm = this.$el.querySelector(formElement)
      updateForm.submit()

      for (const memo of this.allMemos) {
        if (memo.id === id) {
          memo.content = content
          memo.isEditing = false
        }
      }
      localStorage.setItem(id, content)
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
        <template v-if="memo.isEditing">
          <MemoEditForm
            :id="memo.id"
            v-model:content="memo.content"
            @updateMemo="updateMemo"
          ></MemoEditForm>
        </template>

        <template v-else>
          {{ memo.content }}
          <BaseButton @click="editMemo(memo.id)">編集</BaseButton>
          <BaseButton @click="deleteMemo(memo.id)">削除</BaseButton>
        </template>
      </li>
    </ul>
  </div>
</template>
