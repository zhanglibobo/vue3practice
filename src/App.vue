<template>
  <refAndReactive msg="ref和reactive" />
  <propsAndContext msg="propsAndContext" @fn="fn" :obj="obj" />
  <computedAndWatch />
  <watchEffect />
  <unmounted v-if="show" />
  {{ show }}
  <button @click="show = !show">按钮生命周期</button>
  <shallowReactiveshallowRef />
  <shallowReadonly />
  <toRawAndmarkRow></toRawAndmarkRow>
  <customRef />
  <provideAndInject />
  <Suspense>
    <template v-slot:default>
      <asyncSuspense />
    </template>
    <template v-slot:fallback>
      <div>...加载中</div>
    </template>
  </Suspense>
</template>

<script>
import refAndReactive from './components/refAndReactive.vue';
import propsAndContext from './components/propsAndContext.vue';
import computedAndWatch from './components/computedAndWatch.vue';
import watchEffect from './components/watchEffect.vue';
import unmounted from './components/unmounted.vue';
import shallowReactiveshallowRef from './components/shallowReactiveshallowRef.vue';
import shallowReadonly from './components/shallowReadonly.vue';
import toRawAndmarkRow from './components/toRawAndmarkRow.vue';
import customRef from './components/customRef.vue';
import provideAndInject from './components/provideAndInject.vue';
import asyncSuspense from './components/asyncSuspense.vue';
import { provide, reactive, ref } from 'vue';

export default {
  name: 'App',
  components: {
    refAndReactive,
    propsAndContext,
    computedAndWatch,
    watchEffect,
    unmounted,
    shallowReactiveshallowRef,
    shallowReadonly,
    toRawAndmarkRow,
    customRef,
    provideAndInject,
    asyncSuspense
  },
  setup() {
    /* 
    isRef: 检查一个值是否为一个 ref 对象
    isReactive: 检查一个对象是否是由 reactive 创建的响应式代理
    isReadonly: 检查一个对象是否是由 readonly 创建的只读代理
    isProxy: 检查一个对象是否是由 reactive 或者 readonly 方法创建的代理
    */
    function fn(val) {
      console.log('事件监听', val);
    }
    let obj = reactive({
      name: '哈哈哈'
    });
    let show = ref(true);
    provide('obj', obj);
    return {
      fn,
      obj,
      show
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
