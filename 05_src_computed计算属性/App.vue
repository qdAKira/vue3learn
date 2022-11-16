<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息</h1>
  姓:<input type="text" v-model="person.firstName"/>
  <br>
  名:<input type="text" v-model="person.lastName"/>
  <br>
  <span>全名：{{person.fullName}}</span>
  <br>
  全名：<input type="text" v-model="person.fullName"/>
</template>

<script>
import { reactive,computed } from "vue";
export default {
  name: "App",
  setup() {
    // 数据
    let person = reactive({
      firstName:'张',
      lastName:'三'
    })
    // 计算属性--简写（没有考虑计算属性被修改的情况）
    // person.fullName = computed(()=>{
    //   return person.firstName+'-'+person.lastName
    // })

    // 计算属性--完整（考虑计算属性被修改的情况）
      person.fullName = computed({
        get(){
          return person.firstName+'-'+person.lastName
        },
        set(value){
          // split() 方法用于把一个字符串分割成字符串数组
          const nameAttr = value.split('-')
          person.firstName = nameAttr[0]
          person.lastName = nameAttr[1]
        }
    })
    // 返回一个对象（常用）
    return {
      person,
      
    };
  },
};
</script>

<style>
</style>
