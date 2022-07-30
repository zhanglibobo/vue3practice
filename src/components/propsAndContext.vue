<template>
  <div class="child">子组件</div>
  <div class="child">{{ msg }}</div>
  <button class="child" @click="clickFn">按钮传参数给父组件</button>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    msg: [String],
    obj: [Object]
  },
  emits: ['fn'],
  components: {},
  setup(props, context) {
    // props 值为对象，包含组件外部传递过来，且在组件内部声明接收了的属性
    // context 上下文对象
    //         attrs:值为对象，包含嘴贱外部传递过来，但是没有在props配置中声明的属性，相当于this.$attrs
    //         slots：收到的插槽内容，想当与this.$slots
    //         emit:分发自定义事件的函数，相当于this.$emit
    // console.log(props);
    // console.log(context);
    let clickFn = () => {
      context.emit('fn', 1);
    };
    return {
      clickFn
    };
  }
};
</script>

<style scoped>
.child {
  background: #ccc;
}
</style>
