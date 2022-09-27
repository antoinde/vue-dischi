<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from '@/components/MainComponent.vue'

export default {
  name: 'App',
  components:{
    HeaderComponent,
    MainComponent
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/style.scss';

body{
  background-color: var(--spotify-body-main-color);
}


</style>