<template>
    <div class="home container">
        <h1>¡¡Elige un juego y opina!!</h1>
        <GamesGallery :games="this.games">

        </GamesGallery>
    </div>
  </template>

<script>
import GamesGallery from '@/components/GamesGallery.vue';

export default {
        name: 'HomeView',
        data: function(){
            return{
                games: [],
            }
        },
        components: {
            GamesGallery,
        },
        methods: {
            async getGamesInfo(){
                try {
                    let response = await fetch("https://api.rawg.io/api/games?key=cd9f9b1e388841369d0d4fefef7b9cbc&page=1&page_size=20");

                    if(!response.ok){
                        if(response.status ===404){
                            console.error("Juegos no disponibles", response.status);
                            throw new Error("Recurso no encontrado");
                        }
                        else{
                            console.error("Error HTTP", response.status);
                            throw new Error("Erro al obtener personaje");
                        }
                    }

                    const data = await response.json();
                    this.games = data.results
                } catch (error) {
                    console.log(error);
                }
            }

        },
        created(){
            this.getGamesInfo()
        }
    }
</script>

<style scoped>

    h1{
        margin-top: 20px;
        margin-bottom: 40px;
        color: gold;
        justify-content: center;
    }

</style>