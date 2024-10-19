<template>
    <div class="gameCard card" style="width: 16rem;" @click="redirectTo(game.name)">
        <h4 v-if="game.name.length < 20">{{ game.name }}</h4>
        <h5 v-else>{{ game.name }}</h5>
        <img :src="game.background_image" class="card-img-bottom">
    </div>
</template>

<script>
export default{
    name: 'GameCard',
    props: {
        game:{
            type: Object,
            required: true,
        },
    },
    data: function(){
        return{}
    },
    //computed: {},
    methods: {
        redirectTo(gameparam){
            console.log(gameparam)
            this.$router.push('/opinions/'+gameparam)
        },
    },
    //watch: {},
    //components: {},
    //mixins: [],
    //filters: {},
    //-- LifeCycle Methods
    //-- End LifeCycle Methods
}
</script>

<style scoped>
    .gameCard{
        background-color: beige;
        display:flex;
        flex-direction: column;
        border: 4px solid gold;
        margin: 10px;
        border-radius: 8px;
        overflow-y: hidden;
        justify-content: space-between;
    }
    img{
        aspect-ratio: 16/9;
        align-self: flex-end;
        border-top: 4px solid gold;
    }
    h4, h5{
        margin-block-start: 0.5rem;
        color: blue;
    }
</style>