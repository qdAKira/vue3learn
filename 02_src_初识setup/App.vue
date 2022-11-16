<template>
<!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>{{name}}</h1>
  <h1>{{age}}</h1>
  <Button @click="speak">滴滴</Button>
</template>

<script>
import { h } from "vue";
export default {
  name: 'App',
  setup() {
    // 数据
    let name = 'jj';
    let age = '18';
    // 方法
    function speak(){
      alert(`我是${name},今年${age}`)
    }
    // 返回一个对象（常用）
    return {
      name,
      age,
      speak
    }

    // 返回一个渲染函数
    // return ()=> h('h1','哈哈哈')
  }
}
</script>

<style>

</style>
