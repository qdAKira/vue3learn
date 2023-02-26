<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h3>x的值为：{{x.y}}</h3>
  <br>
  <h3>{{person}}</h3>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄：{{ age }}</h2>
  <h2>工资：{{ job.j1.salary }}k</h2>
  <button @click="name += '~'">点我修改姓名</button>
  <button @click="age++">点我修改年龄</button>
  <button @click="job.j1.salary++">点我修改工资</button>
</template>

<script>
import { toRefs,reactive,shallowRef,shallowReactive } from "vue";
export default {
  name: "Demo",
  setup() {
    // 数据
    /* 
       readonly: 让一个响应式数据变为只读的（深只读）。
       shallowReadonly：让一个响应式数据变为只读的（浅只读） 
    */
    let person = shallowReactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    let x = shallowRef({
      y:0
    })
    // 返回一个对象（常用）
    return {
      person,
      // name:toRef(person,'name')
      // 三点运算符，将person对象中第一层数据展开到列出
      ...toRefs(person),
      x
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