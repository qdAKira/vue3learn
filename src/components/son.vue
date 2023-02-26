<template>
  <div class="son">
    <h2>我是孙组件son</h2>
    <h3>{{car.name}}---{{car.price}}</h3>
  </div>
</template>

<script>
import {inject} from 'vue'
export default {
  name:'Son',
  setup() {
    // inject(name) 一般需要传一个值name,为provide中第一个值设置的name
    let car = inject('car1')
    return {
      car
    }
  }
}
</script>

<style scoped>
  .son{
    background-color:skyblue;
    padding: 10px;
  }
</style>