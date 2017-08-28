<template>
  <div class="main">
   <div class="tab">
     <ul>
       <li v-for="(tab,index) in tabList"  @click="currentView = tab,addClassRed(index)" :class="{active:index==num}" >{{tab}}</li>
     </ul>
   </div>
    <div>
      <component :is="currentView"></component>
    </div>
  </div>
</template>

<script>
  import page1 from '@/components/pages/page1'
  import page2 from '@/components/pages/page2'
  import page3 from '@/components/pages/page3'
  export default {
    name: 'main',
    data() {
      return {
        message: 'this is Main',
        currentView:'home',
        active:true,
        tabList:['Home','New','Focus'],
        num:0
      }
    },
    methods:{
      addClassRed (index) {
        this.num=index
        console.log(index)
        console.log(this.num)
      }
    },
    components: {
      Home: page1,
      New: page2,
      Focus: page3
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  .main {
   .tab{
     width:100%;
     height: 50px;
     ul {
       width:100%;
       display: block;
       li{
         list-style: none;
         float: left;
         padding: 10px;
         margin: 10px;
         width:calc(100vw/3 - 80px);
         color: #fff;
         background-color: cornflowerblue;
         height: 20px;
         line-height: 20px;
       }
       .active{
         background-color: #ED3E37;
       }
     }
   }
  }

</style>
