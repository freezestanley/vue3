<template>
    <section>
        <div>子组件</div>
        <com-achild/>
    </section>
</template>

<script>
import ComAchild from "./Achild.vue";
export default {
    components:{
        ComAchild,
    },
};
</script>