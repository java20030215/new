<template>
    <PropsSon :msg="Msg"/>
  </template>
  <script>
  import PropsSon from "./PropsSon.vue";
  
  export default {
    props: {
      msg: {
        type: String,
        default: "",
        required: true,
      },
    },
    data() {
      return {
        h1Ref: null,
      };
    },
    computed: {
      computedMsg() {
        return this.msg + "xx";
      }
    },
    components: {
      PropsSon
    }
  };
  </script>
  
  <style scoped></style>
  