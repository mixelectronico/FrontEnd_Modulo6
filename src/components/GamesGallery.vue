<template>
    <div class="GamesGallery container-fluid">
        <GameComponent v-for="game in games"
                        :key="game.id"
                        :game="game"
                        >
        </GameComponent>
    </div>
</template>

<script>
import GameComponent from './GameComponent.vue';

export default{
    name: 'GamesGallery',
    props: {
        games:{
            type: Array,
            required: true,
        },
    },
    data: function(){
        return{}
    },
    //computed: {},
    //methods: {},
    //watch: {},
    components: {
        GameComponent,
    },
    //mixins: [],
    //filters: {},
    //-- LifeCycle Methods
    //-- End LifeCycle Methods
}
</script>

<style scoped>
    .GamesGallery{
        width: 100%;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-around;
        row-gap: 2rem;
    }
</style>