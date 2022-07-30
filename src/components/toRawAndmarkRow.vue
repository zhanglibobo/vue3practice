<template>
  <div class="container">toRawAndmarkRaw</div>
</template>

<script>
import { isReactive, toRaw, reactive } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    /* toRaw  响应式对象转为普通对象  */
    /* markRaw 标记一个对象使其永远不会成为响应式对象 如；第三方类库，跳过响应式可以提高性能 */
    // let obj = markRaw({
    //   a: {
    //     b: 1
    //   }
    // });
    // console.log(isReactive(obj));
    let obj = toRaw(
      reactive({
        a: {
          b: 1
        }
      })
    );
    console.log(isReactive(obj));
    // return {
    //   obj
    // };
  }
};
</script>

<style scoped></style>
