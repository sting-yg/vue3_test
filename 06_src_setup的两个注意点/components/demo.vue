<template>
    <h1>一个人的信息</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="test">测试触发Demo组建的hello事件</button>
</template>
  
<script>
import { reactive } from 'vue'
  
  export default{
    name: 'AppDemo',
    props: ['msg','school'],
    emits: ['hello'],
    // beforeCreate(){
    //     console.log('----beforeCreate----')
    // },
    setup(props, context){
        console.log('----setup----', props)
        console.log('----setup----', context)
        console.log('----setup----', context.attrs)
        console.log('----setup----', context.emit)
        console.log('----setup----', context.expose)
        console.log('----setup----', context.slots)
      //数据
      let person = reactive({
        name: 'abc',
        age: 18
      })
      //方法
      function test(){
        context.emit('hello',666)
      }
      //返回
      return {
        person,
        test,
      }
    }
  }
</script>
