<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h3>{{person}}</h3>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h2>工资：{{ job.j1.salary }}k</h2>
  <button @click="name += '~'">点我修改姓名</button>
  <button @click="age++">点我修改年龄</button>
  <button @click="job.j1.salary++">点我修改工资</button>
</template>

<script>
import { ref,toRef,toRefs,reactive } from "vue";
export default {
  name: "Demo",
  setup() {
    // 数据
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    // 返回一个对象（常用）
    return {
      person,
      // name:toRef(person,'name')
      // 三点运算符，将person对象中第一层数据展开到列出
      ...toRefs(person)
    };
  },
  // 通过配置项的形式使用生命周期钩子
  // #region
  /* beforeCreate() {
    console.log('---beforeCreate---');
  },
  created() {
    console.log('---created---');
  },
  beforeMount() {
    console.log('---beforeMount---');
  },
  mounted() {
    console.log('---mounted---');
  },
  beforeUpdate() {
    console.log('---beforeUpdate---');
  },
  updated() {
    console.log('---updated---');
  },
  beforeUnmount() {
   console.log('---beforeUnmount---');
 },
 unmounted() {
  console.log('---unmounted---');
 }, */
 //#endregion
};
</script>

<style>
</style>