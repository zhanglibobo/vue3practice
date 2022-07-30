<template>
  <div class="container">readonly</div>
  <button @click="obj.a.b++">{{ obj.a.b }}</button>
</template>

<script>
import { reactive, shallowReadonly } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    let obj = reactive({
      a: {
        b: 1
      }
    });
    obj = shallowReadonly(obj);
    console.log(obj);
    return {
      obj
    };
  }
};
</script>

<style scoped></style>
