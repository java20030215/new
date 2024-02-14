<template>
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer" :msg = "slotMsg"></slot>
  </footer>
</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const slotMsg = '作用域插槽得内容'
</script>