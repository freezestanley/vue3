<template>
  <section>
    <h2>Hello World Vue3.0</h2>
    请输入地址:<input type="text" v-model="city">
    请输入年龄:<input type="text" v-model="age">
     <button @click="stop">不想给你知道我的年龄</button>
    <br/>
  </section>
</template>
<script>
export default {
    setup(){
        const city = ref('上海')
        // const stop = watch(()=>{
        //     console.log("我的年龄在增长:",age.value)
        // },{
        //     lazy: false
        // })

        // const stop = watch(() => age.value, (age, prevAge)=>{
        //     console.log("age:",age,"prevAge",prevAge)
        // })

        const stop = watch([
            () => age.value,
            () => city.value
        ],([age,city],[prevage,prevcity]) => {
            console.log("age:",age,"prevage",prevage)
            console.log("city:",city,"prevcity",prevcity)
        },{
            lazy: true // 是否触发深度监听
        })
        return {
            stop
        }
    }
}
</script>