<template>
  <div class="about">
    <h1>This is an about page</h1>
    <child1 @hook:mounted="childMountedHandle"></child1>
  </div>
</template>
<script>
import child1 from '@/components/child1.vue'
export default {
  name:'about',
  data(){
    return{
      timer:null
    }
  },
  mounted(){
    // 会一直执行下去
    // let timer2 = setInterval(()=>{
    //   console.log('timer2');
    // },2000)
    this.timer = setInterval(()=>{
      console.log('timer');
    },2000)
    this.$once('hook:beforeDestroy',()=>{
      console.log('停止');
      clearInterval(this.timer);
      this.timer = null;
    })
  },
  methods:{
    childMountedHandle(){
      
    }
  }
}
</script>
