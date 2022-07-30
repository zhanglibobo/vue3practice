<template>
  <input type="text" v-model="keyword" />
  <div>{{ keyword }}</div>
</template>

<script>
import { customRef } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    /* 
      customRef：实现一个自定义的ref,并对其依赖项跟踪和更新触发进行显示控制
    */
    function myRef(value, delay) {
      let timer;
      // 通过customRef去实现自定义
      return customRef((track, trigger) => {
        return {
          get() {
            track(); //告诉vue这个value值是需要被‘追踪’的
            return value;
          },
          set(newValue) {
            clearTimeout(timer);
            timer = setTimeout(() => {
              value = newValue;
              trigger(); //告诉vue去更新界面
            }, delay);
          }
        };
      });
    }
    let keyword = myRef('hello', 500);//使用自定义的ref

    return {
      keyword
    };
  }
};
</script>

<style lang="less" scoped></style>
