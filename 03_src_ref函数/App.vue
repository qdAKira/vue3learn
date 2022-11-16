<template>
<!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>{{name}}</h1>
  <h1>{{age}}</h1>
  <Button @click="speak">滴滴</Button>
  <h2>{{job.type}}</h2>
  <h2>{{job.salary}}</h2>
</template>

<script>
import { ref } from "vue";
export default {
  name: 'App',
  setup() {
    // 数据
    let name = ref('jj');
    let age = ref(18);
    let job = ref({
      type:'工程师',
      salary:'30k'
    });
    // 方法
    function speak(){
      name.value = '嘿嘿';
      age.value = 48
      console.log(name,age);
      job.value.type = '色色市'
      console.log(job.value);
    }
    // 返回一个对象（常用）
    return {
      name,
      age,
      speak,
      job
    }

    // 返回一个渲染函数
    // return ()=> h('h1','哈哈哈')
  }
}
</script>

<style>

</style>
