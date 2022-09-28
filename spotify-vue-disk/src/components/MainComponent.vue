<template>
    <main>
        <div class="container">
            <div>
                <SearchGenreComponent :options="genres" @selectedGenre="filterByGenre" />
            </div>
            <AlbumContainerComponent :albums="albumsToDisplay"  />
        </div>
    </main>
</template>

<script>
import AlbumContainerComponent from '@/components/AlbumContainerComponent.vue'
import axios from 'axios';
import SearchGenreComponent from '@/components/SearchGenreComponent.vue'

export default {
    name: 'MainComponent',
    components:{
        AlbumContainerComponent,
        SearchGenreComponent
    },
    data(){
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            selectedGenre: ''
        }
    },
    computed: {
        genres(){ //FUNZIONE CHE MI RESTITUISCE I GENERI DA VISUALIZZARE
            const array = [];
            this.albums.forEach(item => {
                // SCANSIONA TUTTO ALBUM E CONTROLLA I GENERI DEI DISCHI, SALVANDOLI NELL'ARRAY
                if(!array.includes(item.genre)) {
                    array.push(item.genre);
                }
            })
            console.log({genres: array});
            return array;
        },
        albumsToDisplay(){ // CONTIENE SOLO I DISCHI CON IL GENERE SELEZIONATO
            const array = [];
            this.albums.forEach(item => {
                // SCANSIONA TUTTO ALBUM E CONTROLLA I GENERI DEI DISCHI, SALVANDOLI NELL'ARRAY
                if(this.selectedGenre.length=== 0 || this.selectedGenre === item.genre) {
                    array.push(item);
                }
            })

            return array;
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
        },
        filterByGenre(genre) {
            console.log('main received', genre);
            this.selectedGenre = genre;
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