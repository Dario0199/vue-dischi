<template>
  <section>
      <div class="container ">
          <div class="card">

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
    create(){
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
        
    }
</style>