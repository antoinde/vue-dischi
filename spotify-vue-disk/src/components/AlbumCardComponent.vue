<template>
  <div class="card-album">
    <img class="w-100" :src="info.poster" :alt="info.title" @error="replaceWrongImageUrl" />
    <p> {{ info.title }}</p>
    <p class="small-text"> {{ info.author }}</p>
    <p class="small-text"> {{ info.year }}</p>
  </div>
</template>

<script>

import errorImage from '@/assets/img/logo.png'

export default {
    name: 'AlbumCardComponent',
    props:{
        info: Object
    },
    methods:{
        replaceWrongImageUrl(e){
            console.log('errore');
          e.target.src = errorImage
        }
    }
}
</script>

<style lang="scss" scoped>
.card-album{
    display: flex;
    flex-direction: column;
    padding: 20px;
    background-color: var(--spotify-header-card-color);
    color: #ccc;
    text-align: center;
    height: 100%;
  
    &:hover {
      filter: brightness(1.3);
      cursor: pointer;
    }
    p{
        color: #fff;
        text-transform: uppercase;
        margin-top: 5px;
        font-size: 1.3rem;
        font-weight: 600;
    }
    .small-text {
      color: grey;
      font-size: 0.9rem;
    }
}
</style>