<template>
    <section>
        <div v-if="albumsList !== null" class="container d-flex flex-wrap justify-content-center p-0.5">
            <div v-for="(album, index) in albumsList" :key="`album-${index}`" class="cards" >
                <div class="music p-3 text-center">
                    <img class="mb-2" :src="album.poster" :alt="album.title">
                    <h4>{{ album.title }}</h4>
                    <h5>{{ album.author }}</h5>
                    <p>{{ album.year }}</p>
                    <h6>{{ album.genre }}</h6>
                </div>
            </div>
        </div>
        <div v-else class="load">
            <h2>Loading...</h2>
        </div>
    </section>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    data(){
        return{
            albumsList: null,
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
                this.albumsList = result.data.response;
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
        height: 100%;

        .container{
            margin: 0 auto;
            padding-top: 100px;
            padding-bottom: 20px;
        

            .cards{
                width: calc(100% / 8);
                padding: 10px;
                
                

                .music{
                    background: $primary-color;
                    height: 100%;

                    img{
                        width: 100%;
                    }

                    h5,
                    p{
                        color: $text-secondary-color;
                    }
                    
                    h5{
                        font-size: 15px;
                    }

                    p{
                        font-size: 13px;
                    }

                    h4,
                    h6{
                        color: $text-primary-color;
                    }

                    h4{
                        font-size: 17px;
                    }
                }
                

                
            }
        }
        .load{
            width: 100vw;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;

            h2{
                color: $text-primary-color;
            }
        }
    }
</style>