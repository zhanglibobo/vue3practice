<template>
  <div class="container">{{ obj }}inject</div>
</template>

<script>
import { inject } from '@vue/runtime-core';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    const obj = inject('obj');
    return {
      obj
    };
  }
};
</script>

<style scoped></style>
