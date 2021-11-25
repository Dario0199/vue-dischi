<template>
    <section>
        <div class="container-album d-flex flex-wrap justify-content-center p-0.5">
            <div v-for="(album, index) in albumsList" :key="`album-${index}`" class="cards" >
                <div class="music p-3 text-center">
                    <div class="image">
                        <img class="mb-2" :src="album.poster" :alt="album.title">
                    </div>
                    <h4>{{ album.title }}</h4>
                    <h5>{{ album.author }}</h5>
                    <p>{{ album.year }}</p>
                    <h6>{{ album.genre }}</h6>
                </div>
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

        .container-album{
            margin: 0 auto;
            width: 90%;
            padding-top: 100px;
            padding-bottom: 20px;
        }

        .cards{
            width: calc(100% / 8);
            padding: 3px;
            margin-bottom: 10px;
            

            .music{
                background: $primary-color;
                height: 100%;

                img{
                    width: 100%;
                }

                h5,
                p{
                    color: grey;
                }

                h4,
                h6{
                    color: white;
                }
            }
            

            
        }
        
    }
</style>