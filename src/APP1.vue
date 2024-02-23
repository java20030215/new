<template>
    <div>
      <h1>{{ msg }}</h1>
      <h2>{{ count3 }}</h2>
      <div class="card">
        <button type="button" @click="incrementCount">count is {{ count }}</button>
        <button type="button" @click="updateMsg">点击更新msg</button><br/>
        <button type="button" @click="updateLastName">点击更新lastName</button>
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
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        msg: '',
        count: 0,
        count2: 1,
        fullName: {
          firstName: 'John',
          lastName: 'Doe'
        }
      }
    },
    computed: {
      count3() {
        return this.count2 * 2;
      }
    },
    mounted() {
      setInterval(() => {
        this.count2++;
      }, 1000);
    },
    methods: {
      updateMsg() {
        this.$emit('update:msg', 'new msg');
      },
      incrementCount() {
        this.count++;
      },
      updateLastName() {
        this.fullName.lastName = 'xxxx';
      }
    }
  }
  </script>
  
  <style scoped>
  .read-the-docs {
    color: #888;
  }
  </style>
  