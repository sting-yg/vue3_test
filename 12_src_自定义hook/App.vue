<template>
  <button @click="isShowDemo = !isShowDemo">切换隐藏/显示</button>
  <AppDemo v-if="isShowDemo">
  </AppDemo>
  <AppTest v-if="isShowTest">
  </AppTest>
</template>

<script>
import AppDemo from '@/components/Demo.vue'
import AppTest from '@/components/Test.vue'
import { ref } from 'vue'

export default {
  name: 'App',
  components: {
    AppDemo,
    AppTest
  },

  setup() {
    //数据
    let isShowDemo = ref(true)
    let isShowTest = ref(true)
    //返回
    return {
      isShowDemo,
      isShowTest
    }
  }

}
</script>
