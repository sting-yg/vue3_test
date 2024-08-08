<template>
    <h1>Test组件</h1>
    <h2>当前鼠标点击坐标为： x: {{ point.x }}, y: {{ point.y }}</h2>
</template>

<script>
import usePoint from '@/hooks/usePoint'
export default {
    name: 'AppTest',
    setup() {
        const point = usePoint()

        return {
            point
        }
    }
}

</script>