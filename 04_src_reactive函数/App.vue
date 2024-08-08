<template>
  <h1>我是App组件</h1>
  <h2 v-show="person.name">姓名 : {{ person.name }}</h2>
  <h2 v-show="person.gender">性别 : {{ person.gender }}</h2>
  <h2>年龄 : {{ person.age }}</h2>
  <h3>jobType : {{ person.job.type }}</h3>
  <h3>jobSal : {{ person.job.sal }}</h3>
  <h3>job.a.b.c : {{ person.job.a.b.c }}</h3>
  <h3>hobby : {{ person.hobby }}</h3>

  <button @click="Test">测试按钮</button>&nbsp;
  <button @click="addGender">添加性别</button>&nbsp;
  <button @click="deleteName">删除姓名</button>&nbsp;
</template>

<script>
import { reactive } from 'vue'

  export default {
    name: 'App',

    setup(){
      let person = reactive({
        name: 'abc',
        age: 18,
        hobby: ['123','456','789'],
        job: {
          type: 'eng',
          sal: 1000,
          a:{
            b:{
              c: 777
            }
          }
        },
      })

      //方法
      function Test(){
        person.name = 'efg'
        person.age = 81
        person.hobby[0] = 'xuexi'
        person.job.type = 'math'
        person.job.sal = '2000'
        person.job.a.b.c = 999
      }

      function addGender(){
        person.gender = '男'
      }

      function deleteName(){
        delete person.name
      }

      //返回
      return {
        person,
        Test,
        addGender,
        deleteName,
      }
    }
  }
</script>

<style>
</style>
