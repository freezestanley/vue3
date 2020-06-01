<template>
    <section>
        <h2>我是:{{userName}}</h2>
        <h3>city: {{city}}</h3>
        <h4>{{title}}</h4>
        <h5>{{Msg}}</h5>
        <button @click="getUserInfo">你来自哪里？</button>
        <div>{{data}}</div>
        <h3>转换reactive类型数据{{userInfo.userName}}</h3>
        <h3>转换reactive类型数据{{code}}</h3>
    </section>
</template>
<script>
import { ref, onMounted, isRef, reactive,toRefs } from 'vue';

export default {
    props:{
        userName: String
    },
    setup(props, context) {
        console.log(`props: ${props.userName}`)
        console.log(`context: ${context}`)
        const city = ref("")
        const Msg=ref("123123123");
        const getUserCity = () => {
            city.value="上海";
        }
        const getUserInfo = ()=>{
            if (isRef(props.userName)){
                Msg.value = `my name ${userName.value}, from ${city.value}`
            } else {
                Msg.value = `0000`
            }
        }

        onMounted(() => {
            console.log('onMounted')
            // title = '1111111'
        })

        const data=reactive({
            userInfo:{
                userName:"虎克小哥哥"
            },
            code:200
        });

        return {
            city,
            getUserCity,
            title: 'adsasdf',
            getUserInfo,
            Msg,
            ...toRefs(data)
        }
    }
}
</script>