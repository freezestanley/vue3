<template>
    <section>
        <com-a ref="comRef"/>
    </section>
</template>
<script>
import { ref, onMounted } from "vue"
import ComA from "./components/inject/A.vue"
export default {
    components:{
        ComA,
    },
    setup(){
        const comRef = ref(null);
        onMounted(() => {
            console.log(comRef.value.getName())
        })
        return {
            comRef
        }
    }
}
</script>