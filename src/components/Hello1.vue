<template>
    <div>
      <h1>{{ msg }}</h1>
      <h2>{{ count3 }}</h2>
      <div class="card">
        <button type="button" @click="incrementCoun">更改数值 {{ count }}</button>
        <button type="button" @click="updateMsg">点击更新msg</button><br/>
        <button type="button" @click="updateLastName">点击更新lastName</button>
        <p style="color: red;">fullName: {{ fullName.firstName }} {{ fullName.lastName }}</p>
      </div>
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
    console.log('------------> mounted')
      setInterval(() => {
        this.count2++;
      }, 1000);
    },
        beforeMount() {
        console.log('------------> beforeMount')
    },
    updated() {
        console.log('------------> updated')
    },
    beforeUnmount() {
        console.log('------------> beforeUnmount')
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
  