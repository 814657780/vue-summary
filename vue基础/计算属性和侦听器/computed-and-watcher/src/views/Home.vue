<template>
  <div class="home">
    <p>fullname：{{fullname}}</p>
    <p>newname：{{newname}}</p>
    <p>newname2：{{newname2}}</p>
    <br/>
    <button @click="changeComputedName">changeComputedName</button>
    <br/>
    <br/>
    <button @click="changeWatcherName">changeWatcherName</button>
    <br/>
    <br/>
    <button @click="changeFirstName">changeFirstName</button>
  </div>
</template>

<script>
// @ is an alias to /src
// 主要是computed中Getter和setter的对比，以及computed和watcher的对比
export default {
  name: 'Home',
  data(){
     return {
       firstname:'祖国',
       lastname:'强大',
       newname:'没变化1',
       newname2:'没变化2',
       watcherName:'我是watcher'
     }
  },
  computed:{
     fullname:{
       get(){
         console.log('触发getter属性');
         return this.firstname+''+this.lastname
       },
      //  set是fullname直接改变的时候触发，例如给fullname='12 34'直接这样赋值会触发，
      //  但是如果是因为firstname和lastname的改变导致的fullname的变化，是不会触发setter的。
       set(newValue,oldValue){
         console.log(newValue);
         console.log(oldValue);
         var names = newValue.split(' ')
         this.newname = names[0]
         this.newname2 = names[names.length - 1]
       }
     }
  },
  watch:{
     watcherName(newValue,oldValue){
         console.log(newValue);
         console.log(oldValue);
         this.newname="通过watcher改变";
         this.firstname="通过watcher改变2";
     },
     //  有时候需要监听到computed中的数据的变化，进而做一些操作。所以要合理搭配使用。
     fullname(newValue,oldValue){
       console.log(newValue);
       console.log(oldValue);
       console.log('在watch中监听到了computed中fullname的变化');

     }
  },
  methods:{
    changeComputedName(){
       this.fullname = '我爱祖国'+' '+Math.random()
    },
    changeWatcherName(){
       this.watcherName = '我爱 家乡'
    },
    changeFirstName(){
       this.firstname = '我爱家乡'
    }
  }
}
</script>
