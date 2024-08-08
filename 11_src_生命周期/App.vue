<template>
  <button @click="isShowDemo = !isShowDemo">切换隐藏/显示</button>
  <AppDemo v-if="isShowDemo">
  </AppDemo>
</template>

<script>
import AppDemo from './components/demo.vue'
import { ref } from 'vue'

export default {
  name: 'App',
  components: { AppDemo },

  setup() {
    //数据
    let isShowDemo = ref(true)
    //返回
    return {
      isShowDemo
    }
  }

}
</script>

<style></style>
