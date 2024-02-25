<template>
  <p>
    Ask a yes/no question:
    <input v-model="question" :disabled="loading" ref="inputRef" />
  </p>
  <p>{{ answer }}</p>
</template>

<script>
import { ref, watch, onMounted } from 'vue'

export default {
  data() {
    return {
      question: '',
      answer: 'Questions usually contain a question mark. ;-)',
      loading: false,
      inputRef: null
    }
  },
  mounted() {
    this.$nextTick(() => {
      console.log("🚀 ~ onMounted: ", this.$refs.inputRef)
      this.inputRef?.focus()
    })
  },
  watch: {
    question(newQuestion, oldQuestion) {
      if (newQuestion.includes('?')) {
        this.loading = true
        this.answer = 'Thinking...'
        fetch('https://yesno.wtf/api')
          .then(res => res.json())
          .then(data => {
            this.answer = data.answer
          })
          .catch(error => {
            this.answer = 'Error! Could not reach the API. ' + error
          })
          .finally(() => {
            this.loading = false
          })
      }
    }
  }
}
</script>

<style>
/* Add your styles here */
</style>
