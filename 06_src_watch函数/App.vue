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
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    //  情况1：监视ref所定义的一个响应式数据
    // watch(sum,(newValue,oldValue)=>{
    //   console.log('sum变了',newValue,oldValue);
    // })

    //  情况2：监视ref所定义的多个响应式数据
    // watch([sum, msg], (newValue, oldValue) => {
    //   console.log("sum或者msg变了", newValue, oldValue);
    // },{immediate:true});

    /* 
        情况3：监视reactive所定义的一个响应式数据的全部属性，
            1.注意：此处无法正确获取oldValue
            2.注意：强制开启了深度监视（deep配置无效）
      */
    /*  watch(person,(newValue, oldValue)=>{
        console.log('person变了',newValue, oldValue);
      },{deep:false}) //此处的deep配置无效  */

      // 情况4：监视reactive所定义的一个响应式数据的某个属性
      /* watch(()=>person.name,(newValue, oldValue)=>{
        console.log('person的name变了',newValue, oldValue);
      }) */

      // 情况5：监视reactive所定义的一个响应式数据的某些属性
      watch([()=>person.name,()=>person.age],(newValue, oldValue)=>{
        console.log('person的name或者age变了',newValue, oldValue);
      })

      // 特殊情况
       watch(()=>person.job,(newValue, oldValue)=>{
        console.log('person的job变了',newValue, oldValue);
      },{deep:true}) //此处由于监视的是reactive所定义的对象中的某个属性，所以deep配置有效

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
