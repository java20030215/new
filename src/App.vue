<template>
  <router-view></router-view>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <Hello1 :msg="msg" />
  <PropsSon2 title=""/>

</template>

<script>
import Hello1 from './components/Hello1.vue';
import PropsSon2 from './components/PropsSon2.vue';
export default {
  data() {
    return {
      msg: 'Vite + Vue--------APP'
    };
  },
  components: {
    Hello1,PropsSon2
  },
  mounted() {
    console.log('------------>propsRef', this.$refs.propsRef);
    console.log('-------------->watchRef', this.$refs.watchRef);
  }
}
</script>

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
