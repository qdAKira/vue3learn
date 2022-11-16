<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>当前求和为：{{ sum }}</h1>
  <button @click="sum++">点我加1</button>
  <hr />
  <h2>当前信息为：{{ msg }}</h2>
  <button @click="msg += '!'">点我修改信息</button>
  <hr />
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <h2>工资：{{ person.job.j1.salary }}k</h2>
  <button @click="person.name += '~'">点我修改姓名</button>
  <button @click="person.age++">点我修改年龄</button>
  <button @click="person.job.j1.salary++">点我修改工资</button>
</template>

<script>
import { ref, watch, reactive } from "vue";
export default {
  name: "App",
  setup() {
    // 数据
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = ref({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    console.log(person);
    console.log(msg);
    // ref所监视的数据为RefImpl，person.value后相当于监视reactive定义Proxy
    watch(person.value,()=>{
      console.log('person中数据发生改变');
    })
// reactive定义的数据会强制开启了深度监视
    // 返回一个对象（常用）
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>

<style>
</style>
