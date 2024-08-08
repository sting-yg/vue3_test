<template>
  <h1>我是App组件</h1>
  <h2>姓名 : {{ name }}</h2>
  <h2>年龄 : {{ age }}</h2>
  <h3>jobType : {{ job.type }}</h3>
  <h3>jobSal : {{ job.sal }}</h3>
  <button @click="Test">Test</button>
</template>

<script>
import { ref } from 'vue'

  export default {
    name: 'App',

    setup(){

      //数据
      let name = ref('abc')
      let age = ref(18)
      let job = ref({
        type: "eng",
        sal: 1000
      })

      //方法
      function Test(){
        name.value = 'efg'
        age.value = 81
        job.value.type = 'math'
        job.value.sal = '2000'

        console.log(name)
        console.log(age)
      }

      //返回
      return {
        name,
        age,
        job,
        Test,
      }
    }
  }
</script>

<style>
</style>
