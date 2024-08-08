<template>
    <h2>当前求和为： {{ sum }}</h2>
    <button @click="sum++">点我+1</button>
    <hr />
    <h2>当前信息为： {{ msg }}</h2>
    <button @click="msg += '!'">修改信息</button>
    <hr />
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <h2>薪资：{{ person.job.j1.salery }}K</h2>
    <button @click="person.name += '~'">修改姓名</button>
    <button @click="person.age++">修改年龄</button>
    <button @click="person.job.j1.salery++">增薪</button>
</template>
<script>

import { ref, reactive, watchEffect } from 'vue';

export default {
    name: 'appDemo',

    setup() {
        //数据
        let sum = ref(0)
        let msg = ref('你好啊')
        let person = reactive({
            name: 'name',
            age: 18,
            job: {
                j1: {
                    salery: 20
                }
            }
        })
        //监视
        watchEffect(() => {
            const x1 = sum.value
            const x2 = person.job.j1.salery
            console.log(x1)
            console.log(x2)
            console.log('watchEffect 所执行的回调执行了')
        })
        //返回
        return {
            sum,
            msg,
            person,
        }
    }
}
</script>
