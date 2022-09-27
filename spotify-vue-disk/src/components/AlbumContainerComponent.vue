<template>
    <div class="album-container">
        <div class="row">
            <div v-for="album in albums" :key="album.title"  class="ac-fifth-col">
                <!--<album-card-component :info="album"></album-card-component>-->
                <AlbumCardComponent :info="album" /> <!-- <--- da preferire -->
            </div>
        </div>
    </div>
</template>

<script>
import AlbumCardComponent from './AlbumCardComponent.vue'
export default {
    name: 'AlbumContainerComponent',
    props: {
        albums: Array
    }, 
    components: {
        AlbumCardComponent 
    },
}
</script>

<style lang="scss" scoped>
.album-container{
    padding-top: 50px;
    padding-bottom: 50px;
    .row{
        row-gap: 20px;
    }
}
.ac-fifth-col{
    width: calc(100% / 5);
}
</style>