<template>
    <div class="container">
        <div class="row row-cols-5 justify-content-center">
            <div v-for="(disc, index) in filteredGen" :key="index" class="text-center g-5">
                <div class="box">
                    <img :src="disc.poster" :alt="disc.title">
                    <h3>{{disc.title}}</h3>
                    <span>{{disc.author}}</span>
                    <span>{{disc.year}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import {eventBus} from '../main.js'
import {eventBusT} from '../main.js'
export default {
    name: 'DiskList',
    data(){
        return {
          apiPath : 'https://flynn.boolean.careers/exercises/api/array/music',
          discList : '',
          setGen: 'All',
        }
    },
    created(){
        this.getDisk()
        
        eventBusT.$on('gener', element => {
        this.setGen = element
        })
        
    },

    computed: {
    filteredGen(){
      if (this.setGen=='All') return this.discList
      return this.discList.filter(element => element.genre == this.setGen)
      
    }
  },

    methods: {
        getDisk(){
            axios
             .get(this.apiPath)
             .then(res=>{
                this.discList = res.data.response;
                eventBus.$emit('generes', this.discList)
                })
             .catch(error => {
                console.log('Errore: ', error);
                });
        }
    }
}
</script>

<style scoped lang="scss">
    .row {
        .box{
            background: #2e3a46;
            padding: 20px;
            height: 100%;
            img {
                width: 100%;
            }
            h3 {
                color: white;
                margin: 8px 0;
            }
            span {
                display: block;
            }
        }
    }
</style>