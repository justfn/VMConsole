<!-- 值打印 
  
-->
<template lang="html"> 
<div v-if="logValue===true" class="__vmc_Log" >
  <div class="_vmc_objTl" @click="showObjKeys">
    <span class="unfoldIcon" :data-rotate="isShow">▶</span>
    {{Object.prototype.toString.call(logVal).slice(8,-1)}}
  </div>
  <VCMObjLog v-if="isShow" :objVal="logVal" ></VCMObjLog>
  <!-- <VCMObjLog v-if="isShow" :objVal="currentObj" ></VCMObjLog> -->
</div>
<span v-else class="_vmc_strLog">{{logValue}}</span>
</template> 

<script> 
import VCMObjLog from '../../components/VMCObjLog.vue';
export default {
  name: 'VMCLog',
  components: { VCMObjLog, },
  props: {
    logVal: {
      default(){ return '默认值为undefined'; },
    },
  },
  data(){
    return {
      // currentObj: '', 
      
      isShow: false, 
    };
  },
  computed: {
    logValue(){
      if ( this.logVal==='默认值为undefined' ) { return 'undefined'; }
      else if ( this.logVal===null ) { return 'null'; }
      else if ( typeof this.logVal==='number' ) { return this.logVal+''; }
      else if ( typeof this.logVal==='string' ) { return this.logVal; }
      else if ( typeof this.logVal==='boolean' ) { return this.logVal+''; }
      else if ( typeof this.logVal==='function' ) { return this.logVal.toString(); }
      
      return true;
    },
  },
  // beforeCreate(){
  //   this.$options.components.VCMObjLog = require('./Obj.vue').default
  // },
  methods: {
    showObjKeys(){
      this.isShow = !this.isShow; 
      // if (!this.currentObj) {
      //   this.currentObj = this.logVal;
      // }
    },
  },
};
</script> 

<style scoped> 
  ._vmc_strLog {
    display: inline-block;
    margin-left: 1em;
    max-width: 100vw;
    max-height: 50vw;
    overflow: auto;
    vertical-align: bottom;
  }
</style> 
<style> 
</style> 
