<template>
  <section>
   <div>孙子组件</div>
   <img style="width:50px;height:50px" :src="pic"/>
  </section>
</template>

<script>
import { inject } from 'vue'
export default {
  setup() {
    //A组件获取父组件传递过来的帅气头像数据
    const pic = inject('pic')
    return {pic}
  },
};
</script>
