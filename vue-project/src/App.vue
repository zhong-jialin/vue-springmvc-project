<template>
  <div>

<!--    <element-view></element-view>-->
      <emp-view></emp-view>
  </div>
</template>

<script>
// import ElementView from './views/element/ElementView.vue';
import EmpView from "@/views/tlias/EmpView.vue";
  export default{
    components:{
      // ElementView
        //员工页面
        EmpView
    },
    data(){
      return{
        message:"hell1111o vue"
      }
    },
    methods:{

    }
  }
</script>

<style>

</style>
