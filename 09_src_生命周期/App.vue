<template>
  <button @click="isShowDemo=!isShowDemo">切换隐藏或显示</button>
  <Demo v-if="isShowDemo"/>
</template>

<script>
import Demo from './components/demo.vue'
import { ref } from "vue";
export default {
  name: "App",
  components:{Demo},
  setup() {
    let isShowDemo = ref(true)
    return {isShowDemo}
  }
};
</script>

<style>
</style>
