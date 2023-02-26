<template>
  <div class="app">
    <h2>我是祖组件APP</h2>
    <Demo/>
  </div>
</template>

<script>
import Demo from './components/child.vue'
import { ref,provide } from "vue";
export default {
  name: "App",
  components:{Demo},
  setup() {
    let car = ref({
      name:'宝马',
      price:'40w'
    })
    // provide(name,value) 传递2个值，第一个是所要传递值的name,第二个为所传值的value
    provide('car1',car)
    return {car}
  }
};
</script>

<style scoped>
  .app{
    background-color: gray;
    padding: 10px;
  }
</style>
