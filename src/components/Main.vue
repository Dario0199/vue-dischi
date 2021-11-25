<template>
    <section>
        <div class="container d-flex">
            <div v-for="(album, index) in albumsList" :key="`album-${index}`" class="card" >
                <img :src="album.poster" :alt="album.title">
                <h3>{{ album.title }}</h3>
                <h5>{{ album.author }}</h5>
                <p>{{ album.year }}</p>
                <h5>{{ album.genre }}</h5>
            </div>
        </div>

    </section>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    data(){
        return{
            albumsList: [],
        };
    },
    created(){
        this.getAlbums();
    },
    methods:{
        getAlbums(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(result => { 
                console.log(result.data);
                this.albumsList = result.data;
            })
            .catch(error => console.log(error.data))
        }
    }
}
</script>

<style scoped lang="scss">
@import '@/style/variables';
    section{
        background: $secondary-color;
        height: 100vh;

        .container{
            padding-top: 100px;
        }

        .card{
            width: calc(100% / 8);
        }
        
    }
</style>