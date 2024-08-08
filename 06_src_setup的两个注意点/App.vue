<template>
  <AppDemo @hello="showHelloMsg" msg="123" school="456">
    <span>slot</span>
  </AppDemo>
</template>

<script>
import AppDemo from './components/demo.vue'

  export default{
    components: { AppDemo },
    name: 'App',

    setup(){
      function showHelloMsg(value){
        alert(`接收到的数据：${value}`)
      }

      return{
        showHelloMsg
      }
    }
  }
</script>

<style>
</style>
