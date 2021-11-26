<template>
  <header>
      <img src="../assets/logo (1).png" alt="spotify">
      <select @click.prevent="$emit('genList', valGenre)">
          <option value="">All genre</option>
          <option value="Pop">Pop</option>
          <option value="Rock">Rock</option>
          <option value="Metal">Metal</option>
          <option value="Jazz">Jazz</option>
      </select>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return{
            valGenre: '',

        }
    },
    
}
</script>

<style scoped lang="scss">
@import '@/style/variables';

header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: $primary-color;

    img{
        width: 60px;
        padding: 5px
    }
    select{
        width: 100px; 
        height: 30px;
        margin-right: 5px;
        background: $text-primary-color;
        border-radius: 20px;
        border: none;
    }
}
</style>