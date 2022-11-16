<template>
<!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>{{person.name}}</h1>
  <h1>{{person.age}}</h1>
  <Button @click="speak">滴滴</Button>
  <h2>{{person.job.type}}</h2>
  <h2>{{person.job.salary}}</h2>
  <h2>{{person.hobby}}</h2>
</template>

<script>
import { reactive } from "vue";
export default {
  name: 'App',
  setup() {
    // 数据
    let person = reactive({
      name:'张三',
      age:18,
      job:{
        type:'工程师',
        salary:'30k'
      },
      hobby:['吃','喝','玩']
    })
    // 方法
    function speak(){
      console.log(person);
      person.name = '李四'
      person.age = 48
      person.job.salary = '40k'
      person.hobby[0] = '飘'
      
    }
    // 返回一个对象（常用）
    return {
      person,
      speak
    }

    // 返回一个渲染函数
    // return ()=> h('h1','哈哈哈')
  }
}
</script>

<style>

</style>
