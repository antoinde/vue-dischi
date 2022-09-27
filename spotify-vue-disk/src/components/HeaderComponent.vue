<template>
  <header>
    <img src="../assets/img/logo.png" alt="Vue Dischi"/>

  </header>
</template>

<script>
export default {
    name: 'HeaderComponent'
}
</script>

<style lang="scss" scoped>
header{
    height: 80px;
    background-color: var(--spotify-header-card-color);
    padding: 10px;
    img {
      height: 60px;
    }
}
</style>