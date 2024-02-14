<script setup lang="ts">
import { ref,reactive, computed,onBeforeMount,onMounted,onUpdated,onUnmounted } from 'vue'

onBeforeMount(()=>{
  console.log('------------> onBeforeMount')
})
onMounted(()=>{
  console.log('------------> onMounted')
})
onUpdated(()=>{
  console.log('------------> onUpdated')
})
onUnmounted(()=>{
  console.log('------------> onUnmounted')
})
const props = defineProps<{ msg: string }>()

const emits = defineEmits(['update:msg'])



const count = ref(0)

const count2 = ref(1)

const count3 = computed(()=> {
  // 复杂计算
  return count2.value * 2
})
const fullName = reactive({
  firstName: 'John',
  lastName: 'Doe'
})
// const firstName = ref('John')
// const lastName = ref('Doe')
setInterval(()=>{
  count2.value++
},1000)
const updateMsg = ()=>{
  //第一个参数是事件名，第二个参数是事件值
  emits('update:msg', 'new msg')
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <h2>{{ count3 }}</h2>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <!-- <button type="button" @click="count++">count2 is {{ count2 }}</button> -->
    <button type="button" @click="updateMsg">点击更新msg</button><br/>
    <button type="button" @click="()=> fullName.lastName = 'xxxx'">点击更新lastName</button>
    <p style="color: red;">fullName: {{ fullName.firstName }} {{ fullName.lastName }}</p>

    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
