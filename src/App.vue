<template>
    <section>
        <h2>{{userInfo.userName}}</h2>
        <com-user :userName="'虎克小哥哥'"/>
        <computed/>
        <Inject/>
        <ComA/>
    </section>
</template>
<script>
import ComA from './components/inject/A.vue'
import ComUser from './components/user.vue'
import Computed from './components/Computed.vue'
import {
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    onBeforeUnmount,
    onUnmounted,
    onErrorCaptured,
    onRenderTracked,
    onRenderTriggered,
    reactive,
    provide,
    ref
} from "vue";

const pic='https://dss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1461286262,427682797&fm=26&gp=0.jpg'

export default {
    components:{
        ComUser,Computed,ComA
    },
    setup () {
        const userInfo = reactive({userName: "胡可哥"})
        console.log('setup')
        onRenderTriggered(() => {
            console.log('onRenderTracked');
        })
        onRenderTriggered((event) => {
            console.log('onRenderTriggered')
        })
        onBeforeMount(() => {
            console.log('onBeforeMount')
            userInfo.userName = 'sdfasdfsf'
        })
        onMounted(() => {
            console.log('onMounted')
        })
        onBeforeUpdate(()=>{
            console.log('onBeforeUpdate')
        })
        onUpdated(()=>{
            console.log('onUpdated')
        })
        onBeforeUnmount(()=>{
            console.log('beforeDestroy')
        })
        onUnmounted(()=>{
            console.log('onUnmounted')
        })
        onErrorCaptured(() => {
            console.log('onErrorCaptured')
        })

        provide('pic',pic )
        //也支持传递响应式数据
        // const pic = ref('pic');
        // provide('pic',pic)

        return {
            userInfo,
        }
    }
}
</script>
<style>
    body{
        padding: 50px;
        color: #42b983;
        text-align: center;
        background: #282c34;
    }
</style>