<template>
    <div class="row row-cols-5">
        <div v-for="(disc, index) in discList" :key="index" class="col text-center">
            <img :src="disc.poster" :alt="disc.title">
            <h3>{{disc.title}}</h3>
            <p>{{disc.author}}</p>
            <p>{{disc.year}}</p>
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
        .col{
            background: #2e3a46;
            padding: 20px;
            // margin: 50px;
            img {
                width: 100%;
            }
            h3 {
                color: white;
            }
        }
    }
</style>