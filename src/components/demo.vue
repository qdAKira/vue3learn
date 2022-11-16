<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>当前求和为：{{ sum }}</h1>
  <button @click="sum++">点我加1</button>
  <hr>
  <h2>获取数据位置,x:{{point.x}},y:{{point.y}}</h2>
</template>

<script>
import { ref } from "vue";
import usePoint from '../hooks/usePoints'
export default {
  name: "Demo",
  setup() {
    // 数据
    let sum = ref(0);
    let point = usePoint()

    // 返回一个对象（常用）
    return {
      sum,
      point
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