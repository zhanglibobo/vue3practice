<template>
  <div class="container">unmounted组件</div>
  <div>------{{ a }}</div>
</template>

<script>
// import {
//   onBeforeMount,
//   onMounted,
//   onBeforeUpdate,
//   onUpdated,
//   onBeforeUnmount,
//   onUnmounted
// } from 'vue';
import savePoint from './usePoint';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    /*
       beforeCreate、created ==> setup(){}
    */
    // onBeforeMount(() => {
    //   console.log('onBeforeMount');
    // });
    // onMounted(() => {
    //   console.log('onMounted');
    // });
    // onBeforeUpdate(() => {
    //   console.log('onBeforeUpdate');
    // });
    // onUpdated(() => {
    //   console.log('onUpdated');
    // });
    // onBeforeUnmount(() => {
    //   console.log('onBeforeUnmount');
    // });
    // onUnmounted(() => {
    //   console.log('onUnmounted');
    // });
    let a = savePoint();
    console.log(a);
    return {
      a
    };
  }
};
</script>

<style scoped></style>
