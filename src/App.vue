<script setup lang="ts">
import { onMounted, ref, provide } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Watch from "./components/Watch.vue";
import Props from "./components/Props.vue";
import Slot from "./components/Slot.vue";

const msg = ref<string>("Vite + Vue--------APP");
provide("app-msg", msg.value);
const show = ref<boolean>(true);
const propsRef = ref<HTMLElement | null>(null);
const watchRef = ref<HTMLElement | null>(null);
onMounted(() => {
  console.log("------------>propsRef", propsRef.value);
  console.log("-------------->watchRef", watchRef.value);
});
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <!-- <button @click="show = !show">hidden button</button>
  <Props :msg="msg" ref="propsRef" />
  <Watch v-if="show" ref="watchRef" />
  <HelloWorld v-else :msg="msg" @update:msg="($event) => (msg = $event)" /> -->

  <Slot>
    <!-- 简写 -->
    <template #header>
      <Props :msg="msg" ref="propsRef" />
    </template>
    slot得值
    <!-- 作用域插槽 -->
    <template v-slot:footer="slotProps"> Footer{{ slotProps.msg }} </template>
    <!-- 全写 -->
  </Slot>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
