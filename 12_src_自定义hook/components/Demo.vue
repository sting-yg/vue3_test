<template>
    <h1>Demo组件</h1>
    <h2>当前求和为： {{ sum }}</h2>
    <button @click="sum++">点我+1</button>
    <h2>当前鼠标点击坐标为： x: {{ point.x }}, y: {{ point.y }}</h2>
    <hr />
</template>

<script>
import { ref } from 'vue';
import usePoint from '@/hooks/usePoint'

export default {
    name: 'AppDemo',

    setup() {
        //数据
        let sum = ref(0)
        let point = usePoint()

        //返回
        return {
            sum,
            point
        }
    }
}
</script>
