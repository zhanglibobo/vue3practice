<template>
  <div>{{ msg }}</div>
  <div>{{ person.age }}</div>
  <div>{{ age }}</div>
  <div>{{ num }}</div>
  <button @click="num++">按钮+1</button>
  <button @click="age++">按钮+age</button>
</template>

<script>
import { ref, reactive, toRefs } from 'vue';
export default {
  name: 'refAndReactive',
  props: {
    msg: String
  },
  //在beforeCreate之前执行一次，this是undefined
  setup() {
    let num = ref(0);
    num.value++;
    let person = reactive({
      name: 'zhang',
      age: 17
    });
    let person2 = reactive({
      name: 'zhang111',
      age: 18
    });
    return {
      num,
      person,
      ...toRefs(person2)
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
