<template>
  <div id="app">
    <Header />

    <Main :albums="albumsList"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
        return{
          albumsList: null,
          
        };
  },
  created(){
    this.getAlbums();
    this.showList();
  },
  computed:{
    showList(){
      if(this.valGenre === ""){
        return this.albumsList
      }
      return this.albumsList.filter(album => album.genre === this.valGenre);
      console.log(this.albumsList);
    }
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

<style lang="scss">
@import '@/style/global';
</style>
