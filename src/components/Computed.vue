<template>
  <section>
    <h2>Hello World Vue3.0</h2>
    请输入年龄:<input type="text" v-model="age">
    <br/><br/>
    我的年龄是:{{userMsg}}
    <br/>
  </section>
</template>
<script>
import {ref, computed} from "vue";

export default {
    setup () {
        const age = ref("")
        // const userMsg = computed(() =>{
        //     return `my age: ${age.value}`
        // })
        const userMsg = computed({
            get () {
                return `my age: ${age.value}`
            },
            set(val){
                age.value = val
            }
        })
        userMsg.value = "";
        return {
            age,
            userMsg
        }
    }
}
</script>
