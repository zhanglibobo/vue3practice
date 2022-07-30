<template>
  <div>异步组件{{ keyword }}</div>
  <button @click="keyword++">按钮</button>
</template>

<script>
import { ref } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  async setup() {
    let keyword = ref(
      await new Promise(resolve => {
        setTimeout(() => {
          resolve(1);
        }, 1000);
      })
    );
    return {
      keyword
    };
  }
};
</script>

<style lang="less" scoped></style>
