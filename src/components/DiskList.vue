<template>
    <div class="row row-cols-5 g-5">
        <div v-for="(disc, index) in discList" :key="index" class="text-center">
            <img :src="disc.poster" :alt="disc.title">
            <h3>{{disc.title}}</h3>
            <span>{{disc.author}}</span>
            <span>{{disc.year}}</span>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
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

    methods: {
        getDisk(){
            axios
             .get(this.apiPath)
             .then(res=>{
                this.discList = res.data.response;
             })
        }
    }
}
</script>

<style scoped lang="scss">
    .row {
        margin: 50px auto;
        flex-shrink: 1;
        width: 80%;
        .text-center{
            width: 15%;
            background: #2e3a46;
            padding: 20px;
            margin: 20px;
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