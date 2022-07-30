<template>
  <input type="text" v-model="firstName" />
  <br />
  <input type="text" v-model="lastName" />
  <br />
  <div>{{ fullName }}</div>
  <br />
  <br />
  <h3>{{ sum }}</h3>
  <button @click="sum++">按钮+1sum</button>
  <h3>{{ msg }}</h3>
  <button @click="msg += 'pp'">按钮msg</button>
  <h3>{{ obj.age }}</h3>
  <button @click="obj.age++">按钮+1obj</button>
  <h3>{{ obj.job }}</h3>
  <button @click="obj.job.a.b++">按钮+1obj.job</button>
</template>

<script>
import { computed, reactive, toRefs, ref, watch } from 'vue';
export default {
  data() {
    return {};
  },
  components: {},
  setup() {
    let person = reactive({
      firstName: '',
      lastName: ''
    });
    // 计算属性简写
    // let fullName = computed(() => {
    //   return person.firstName + person.lastName;
    // });
    // 计算属性完整
    let fullName = computed({
      get() {
        return person.firstName + '-' + person.lastName;
      },
      set(value) {
        const nameArr = value.split('-');
        person.firstName = nameArr[0];
        person.firstName = nameArr[1];
      }
    });
    /* --------watch---------- */
    // 1、监听ref定义的响应式数据
    let sum = ref(0);
    let msg = ref('h');
    // watch(sum, (newVal, oldVal) => {
    //   console.log('sum变化了' + sum.value, newVal, oldVal);
    // });
    // 2、监听多个ref定义的响应式数据
    // watch([sum, msg], (newVal, oldVal) => {
    //   console.log('sum或者msg变化了', newVal, oldVal);
    // });
    // 3、监听reactive定义的响应式数据
    //    若监视的是reactive定义的响应式数据，则无法正确获得oldValue，强制开始了深度监视
    let obj = reactive({
      name: '找',
      age: 18,
      job: {
        a: {
          b: 1
        }
      }
    });
    // watch(
    //   obj,
    //   (newValue, oldValue) => {
    //     console.log('obj变化了', newValue, oldValue);
    //   },
    //   { immediate: true, deep: false }
    // );
    // 4、监视reactive定义的响应式数据的某个属性,由于监视的是reactive定义的对象中的某个属性，所以deep配置有效(深层要加deep)
    // watch(
    //   () => obj.job,
    //   (newValue, oldValue) => {
    //     console.log('obj.job', newValue, oldValue);
    //   },
    //   { immediate: true, deep: true }
    // );
    // 5、监视reactive定义的响应式数据中的某些属性
    watch(
      [() => obj.job, () => obj.name],
      (newValue, oldValue) => {
        console.log('obj.job', newValue, oldValue);
      },
      { immediate: true, deep: true }
    );

    return {
      ...toRefs(person),
      fullName,
      sum,
      msg,
      obj
    };
  }
};
</script>

<style scoped></style>
