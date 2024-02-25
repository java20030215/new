<template>
  <PropsSon2 title="computedMsg"/>
</template>
<script>
import PropsSon from "./PropsSon.vue";

export default {
  data(){
    return {
      initialMsg: "FFL",
    };
  },
  props: {
    msg: {
      type: String,
      default: "",
      required: true,
    },
  },
  computed: {
    computedMsg() {
      return this.initialMsg + "xx";
    }
  },
  components: {
    PropsSon
  }
};
</script>

<style scoped></style>
