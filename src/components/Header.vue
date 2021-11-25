<template>
  <header>
      <img src="../assets/logo (1).png" alt="spotify">
  </header>
</template>

<script>
export default {
name: 'Header',
}
</script>

<style scoped lang="scss">
@import '@/style/variables';

header{
    background: $primary-color;

    img{
        width: 60px;
        padding: 5px
    }
}
</style>