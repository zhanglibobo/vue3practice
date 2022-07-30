<template>
  <div class="container">shallowReactiveshallowRef</div>
  <button @click="obj.a.b.c++">{{ obj.a.b.c }}</button>
</template>

<script>
import { shallowReactive, shallowRef } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    let obj = shallowReactive({
      //只处理对象最外层属性的响应式
      a: {
        b: {
          c: 1
        }
      }
    });
    let obj2 = shallowRef({
      //只处理基本数据类型的响应式, 不进行对象的响应式处理。
      a: {
        b: {
          c: 1
        }
      }
    });
    console.log(obj);

    return {
      obj,
      obj2
    };
  }
};
</script>

<style scoped></style>
