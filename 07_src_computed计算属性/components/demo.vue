<template>
    <h1>个人信息</h1>
    姓：<input type="text" v-model="person.firstName">
    <br/>
    名：<input type="text" v-model="person.lastName">
    <br/>
    全名：{{ person.fullName }}
    <br/>
    全名：<input type="text" v-model="person.fullName">
</template>

<script>
import { computed, reactive } from 'vue'

    export default{
        name: 'appDemo',
        setup(){
            let person = reactive({
                firstName: 'firstName',
                lastName: 'lastName'
            })

            // let fullName = computed (() => person.firstName + ' ' + person.lastName )
            // person.fullName = computed (() => { return person.firstName + '-' + person.lastName })

            person.fullName = computed({
                get(){
                    return person.firstName + '-' + person.lastName
                },
                set(value){
                    const nameArr = value.split('-')
                    person.firstName = nameArr[0]
                    person.lastName = nameArr[1]
                }
            })

            return{
                person,
            }
        }
    }
</script>

