<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <div class="demo">
    <h2>我是父组件child</h2>
    <Son/>
  </div>
</template>

<script>
import Son from './son.vue'
import { ref, customRef } from "vue";
export default {
  name: "Demo",
  components:{Son},
  setup() {
    // 数据
    
  
    return {
      
    };
  },
};
</script>

<style scoped>
 .demo{
  background-color: #bfa;
  padding: 10px;
 }
</style>