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
import { ref, reactive, watch } from 'vue';

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
        //情况1： 监视ref所定义的一个响应式数据
        // watch(sum,(newValue, oldValue)=>{
        //     console.log('sum 变了', newValue, oldValue)
        // },{immediate: true})

        //情况2： 监视ref所定义的多个响应式数据
        // watch([sum,msg],(newValue,oldValue)=>{
        //     console.log('sum或msg变了', newValue, oldValue)
        // },{immediate: true})

        //情况3：监视reactive所定义的一个响应式数据，
        // 1.注意：此处无法正确获取oldValue
        // 2.注意：强制开启深度监视 （deep配置无效） 2024 已经修改 （deep配置有效）

        // watch(person,(newValue, oldValue)=>{
        //     console.log('person变了', newValue, oldValue)
        // })

        //情况4：监视reactive响应中的某一个数据
        // watch(()=>person.name,(newValue, oldValue)=>{
        //     console.log('person的name变了', newValue, oldValue)
        // })
        // watch(()=>person.age,(newValue, oldValue)=>{
        //     console.log('person的age变了', newValue, oldValue)
        // })

        //情况5：监视reactive所定义的一个响应式数据中的某些属性
        // watch([()=>person.name,()=>person.age],(newValue, oldValue)=>{
        //     console.log('person的 name 或 age 变了', newValue, oldValue)
        // })

        //情况6：特殊情况
        // 1.注意：此处由于监视的是reactive所定义的对象中的某个属性，deep配置默认是false需要deep true 配置
        watch(() => person.job, (newValue, oldValue) => {
            console.log('person的job变了', newValue, oldValue)
        }, { deep: true })
        //返回
        return {
            sum,
            msg,
            person,
        }
    }
}
</script>
