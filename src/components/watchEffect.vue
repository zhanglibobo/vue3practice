<template>
  <div class="container">
    {{ a }}
    <div>--------</div>
    {{ b }}
  </div>
  <button @click="a += 'a'">aaa</button>
  <button @click="b += 'b'">anniubbbb</button>
</template>

<script>
import { watchEffect, ref } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    /* 
       watch：既要指明监视的属性，也要指明监视的回调
       watchEffect：不用指明监视的哪个属性，监视中用到哪个属性，就监视哪个属性
       有点像computed、但是computed注重的是计算出来的值（回调函数的返回值），必须写return
       而watchEffect更注重的是过程（回调函数的函数体），所以不用写返回值
    */
    let a = ref('a');
    let b = ref('b');
    watchEffect(() => {
      const c = a.value + b.value;
      console.log(`改变了a或者b，，，${c}`)
    });
    return {
      a,
      b
    };
  }
};
</script>

<style scoped></style>
