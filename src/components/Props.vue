<template>
  <PropsSon :msg="msg"/>
</template>
<script lang="ts">
import { defineComponent, ref, reactive, computed } from "vue";
import PropsSon from "./PropsSon.vue";
export default defineComponent({
  props: {
    msg: {
      type: String,
      default: "",
      required: true,
    },
  },
  setup(props, ctx) {
    console.log('--------------->ctx',ctx)
    const h1Ref = ref<HTMLHeadingElement | null>(null);
    const computedMsg = computed(() => props.msg + "xx");
    return {
      computedMsg,
      h1Ref
    };
  },
  components:{
    PropsSon
  }
});
</script>
<style lang="scss" scoped></style>
