<template>
  <select @change="a()" name="genra" id="genra" v-model="selectV">
      <option v-for="(gen, i) in this.generS " :key="i" :value="gen">{{gen}}</option>
      
  </select>
</template>

<script>
import {eventBus} from '../main.js'
import {eventBusT} from '../main.js'
export default {
 name: 'Selector',
 
 data(){
     return{
         generS : ['all'],
         selectV : ''
         
     }
     
 },

 created() {
     
     eventBus.$on('generes',array =>{
         array.forEach(element => {
             if (!this.generS.includes(element.genre)){
                 this.generS.push(element.genre)
                 ;
             }
         });
     })
 },
 methods: {
     a(){
         eventBusT.$emit('gener', this.selectV);
     }
     
 }
 
}
</script>

<style>
    select {
        margin-right: 100px;
        color: white;
        background-color: #1e2d3b;
    }
</style>