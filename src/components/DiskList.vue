<template>
    <div class="row row-5">
        <div v-for="(disc, index) in discList" :key="index" class="col-lg">
            <img :src="disc.poster" :alt="disc.title">
            <h3>{{disc.title}}</h3>
            <p>{{disc.author}}</p>
            <p>{{disc.year}}</p>

        </div>
    </div>
    <!-- "poster": "https://images-na.ssl-images-amazon.com/images/I/81r3FVfNG3L._SY355_.jpg",
            "title": "And Justice for All",
            "author": "Metallica",
            "genre": "Metal",
            "year": "1988"
   -->
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

</style>