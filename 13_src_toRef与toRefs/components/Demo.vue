<template>
    <h2>姓名：{{ name}}</h2>
    <h2>年龄：{{ age}}</h2>
    <h2>薪资：{{ salery}}</h2>
    <button @click="name += '~'">修改姓名</button>
    <button @click="age++">修改年龄</button>
    <button @click="salery += 10">修改薪资</button>
</template>

<script>
import { reactive, toRef, toRefs } from 'vue'
export default {
    name: 'AppDemo',

    setup(){
        //数据
        let person = reactive({
            name: 'name',
            age: 1,
            job: {
                j1: {
                    salery: 10
                }
            }
        })

        const name1 = person.name
        console.log('%%%', name1)

        const name2 = toRef(person, 'name')
        console.log('###', name2)

        const x = toRefs(person)
        console.log('***', x)
        

        //返回
        return {
            person,
            name1,
            name2,
            x,
            // name: toRef(person,'name'),
            // age: toRef(person,'age'),
            // salery: toRef(person.job.j1,'salery')
            ...toRefs(person)
        }
    }
}
</script>