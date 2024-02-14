<script setup lang="ts">
import { ref, watch,onMounted } from 'vue'

const question = ref('')//1
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)
//获取到input得dom对象，并设置focus方法
const inputRef = ref<HTMLInputElement | null>(null)
// 可以直接侦听一个 ref
// 监听某个响应式数据，进行一些特定操作，比如说请求接口
watch(question, 
//newQuestion : '1'
//oldQuestion : ''
async (newQuestion, oldQuestion) => {
console.log("🚀 ~ newQuestion:", newQuestion)
console.log("🚀 ~ oldQuestion:", oldQuestion)
  if (newQuestion.includes('?')) {
    loading.value = true
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    //   image.value = (await res.json()).image
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    } finally {
      loading.value = false
    }
  }
})
onMounted(()=>{
    console.log("🚀 ~ onMounted: ", inputRef.value)
    inputRef.value?.focus()
})
defineExpose({
    question,
    inputRef
})
</script>

<template>
  <p>
    Ask a yes/no question:
    <!-- 获取到input得dom对象，并设置focus方法 -->
    <input v-model="question" :disabled="loading" ref="inputRef" />
  </p>
  <p>{{ answer }}</p>
  <!-- <img :src="image"/> -->
</template>