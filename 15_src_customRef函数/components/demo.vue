<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <input type="text" v-model="keyword" />
  <h3>{{ keyword }}</h3>
</template>

<script>
import { ref, customRef } from "vue";
export default {
  name: "Demo",
  setup() {
    // 数据
    // 自定义一个ref--名为：myRef--------track(追踪)  trigger()
    function myRef(value,delay) {
      let timer
      return customRef((track, trigger) => {
        return {
          get() {
            console.log(`有人从myRef这个容器中读取数据了，我把${value}给他了`);
            track(); //通知Vue追踪数据的变化（提前和get进行商量，value是有用的）
            return value;
          },
          set(newValue) {
            console.log(`有人从myRef这个容器中数据改为了：${newValue}`);
            clearTimeout(timer)
            timer = setTimeout(() => {
              value = newValue;
              trigger(); //通知Vue去重新解析模板
            }, delay);
          },
        };
      });
    }
    let keyword = myRef("hello",500);  // 使用程序员自定义的ref
    // let keyword = ref('hello')  //使用Vue提供的ref
    // 返回一个对象（常用）
    return {
      keyword,
    };
  },
};
</script>

<style>
</style>