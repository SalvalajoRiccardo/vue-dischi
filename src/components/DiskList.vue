<template>
    <div class="container">
        <div class="row row-cols-5 justify-content-center">
            <div v-for="(disc, index) in discList" :key="index" class="text-center g-5">
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
// import {eventBusT} from '../main.js'
export default {
    name: 'DiskList',
    data(){
        return {
          apiPath : 'https://flynn.boolean.careers/exercises/api/array/music',
          discList : ''
        }
    },
    created(){
        this.getDisk()
        
        
    },

    // mounted: {
    //     eventBusT.$on('generes', );
    // },

    methods: {
        getDisk(){
            axios
             .get(this.apiPath)
             .then(res=>{
                this.discList = res.data.response;
                eventBus.$emit('generes', this.discList);
             })
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