<template>
    <main>
        <div class="container">
            <AlbumContainerComponent :albums="albums"  />
        </div>
    </main>
</template>

<script>
import AlbumContainerComponent from '@/components/AlbumContainerComponent.vue'
import axios from 'axios';

export default {
    name: 'MainComponent',
    components:{AlbumContainerComponent},
    data(){
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: []
        }
    },
    created(){
       this.getAlbumData();
    },
    methods: {
        getAlbumData(){
            axios.get(this.apiUrl)
                .then((response)=>{
                    if (this.isResponseOK(response)){
                        console.log(response.data)
                        this.albums = response.data.response;
                    }
                })
                .catch((e)=>{
                    console.log(e);
                });
        },
        isResponseOK({status}){
            return status === 200;
        }
    }
}
</script>

<style lang="scss" scoped>
main{
    background-color: var(--spotify-body-main-color);
    color: #fff;
}
</style>