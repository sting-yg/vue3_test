<template>
  <h1>我是App组件</h1>
  <h2>姓名： {{ name }}</h2>
  <h2>年龄 ： {{ age }}</h2>
  <button @click="funTest1">funTest1</button>
  <br>
  <br>
  <button @click="funTest2">funTest2</button>
  <br>
  <br>
  <button @click="test1">test1</button>
  <br>
  <br>
  <button @click="test2">test2</button>
</template>

<script>
  export default {
    name: 'App',

    data(){
      return{
        gender: '男',
        a: 100
      }
    },
    methods:{
      funTest2(){
        alert('methods function \n gender : ' + this.gender )
      },
      test1(){
        console.log(this.gender)
        this.funTest2
        console.log(this.name)
        console.log(this.age)
        this.funTest1
      }
    },
    setup(){
      //数据
      let name = 'abc'
      let age = 18
      let b = 200
      //方法
      function funTest1(){
        alert(`setup function \n name : ${name} \n age : ${age}`)
      }
      function test2(){
        console.log(name)
        console.log(age)
        funTest1
        console.log(this.gender)
        this.funTest2
      }
      return {
        name,
        age,
        funTest1,
        test2,
        b
      }
    }
  }
</script>

