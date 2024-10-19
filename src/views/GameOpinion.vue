<template>
    <div class="gameOpinion container">
        <h1>{{ gameName }}</h1>
        <div v-if="opinionList.length > 0" class="opinionList">
            <div v-for="opinion in opinionList" class="opinionElement" :key="opinion.id">
                <div class="username">
                    <h5>{{ opinion.uName }}</h5>
                    <div class="opinionPanel">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-pencil-fill" viewBox="0 0 16 16" @click="editOpinion(opinion.opinionId)">
                            <path d="M12.854.146a.5.5 0 0 0-.707 0L10.5 1.793 14.207 5.5l1.647-1.646a.5.5 0 0 0 0-.708zm.646 6.061L9.793 2.5 3.293 9H3.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.207zm-7.468 7.468A.5.5 0 0 1 6 13.5V13h-.5a.5.5 0 0 1-.5-.5V12h-.5a.5.5 0 0 1-.5-.5V11h-.5a.5.5 0 0 1-.5-.5V10h-.5a.5.5 0 0 1-.175-.032l-.179.178a.5.5 0 0 0-.11.168l-2 5a.5.5 0 0 0 .65.65l5-2a.5.5 0 0 0 .168-.11z"/>
                        </svg>
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-trash-fill" viewBox="0 0 16 16" @click="deleteOpinion(opinion.id)">
                            <path d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5M8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5m3 .5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 1 0"/>
                        </svg>
                    </div>
                </div>
                <div class="opinion"><p>{{ opinion.uOpinion }}</p></div>
            </div>
        </div>
        <div v-else class="alert alert-info nopinions">
            <h1>No hay opiniones para mostrar<br>¡¡Pero tu puedes escribir una!!</h1>
        </div>
        <div class="formulario">
            <div class="input-group mb-3">
                <span class="input-group-text">Yo soy</span>
                <input v-model="userName" type="text" class="form-control text-center" aria-label="Amount (to the nearest dollar)" placeholder="Nombre de usuario">
                <span class="input-group-text">y opino que...</span>
            </div>
            <div class="input-group mb-3">
                <textarea v-model="userOpinion" class="form-control" aria-label="With textarea" placeholder="Escribe tu opinión aquí"></textarea>
                <button class="btn btn-primary" type="button" id="button-addon2" @click.prevent="addOpinion" >Enviar</button>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'GameOpinion',
    //props: {},
    data: function(){
        return{
            userName: '',
            userOpinion: '',
            opinionCounter: 0,
            opinionList:[],
        }
    },
    computed: {
        gameName(){
            let name = this.$route.params.gameName;
            console.log(name)
            return name
        }
    },
    methods: {
        addOpinion(){
            let uName = this.userName
            let uOpinion = this.userOpinion
            this.opinionCounter++
            let opinionId = this.opinionCounter
            this.opinionList.push({opinionId, uName, uOpinion})
            this.userName = "";
            this.userOpinion = "";
        },
        editOpinion(id){
            alert(id)
            this.userName = this.opinionList[id-1].uName
            this.userOpinion = this.opinionList[id-1].uOpinion
        },
        deleteOpinion(id){
            alert(id)
            this.opinionList.pop(id)
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

    h1{
        margin-top: 20px;
        margin-bottom: 40px;
        color: gold;
        justify-content: center;
    }

        textarea{
            field-sizing: content;
        }

    .nopinions h1{
            color: blue;
    }

    .opinionList{
        display: flex;
        flex-direction: column;
        width: auto;
        margin-bottom: 40px;
    }   
    
    .opinionElement{
        display: flex;
        flex-direction: row;
        width: auto;
        height: fit-content;
        border: 2px solid gold;
        border-radius: 12px;
        margin-block: 5px;
    }

    .username{
        width: 200px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin-right: 0;
        padding: 10px;
    }

    h5{
        width: 100%;
        color: beige;
    }

    .opinionPanel{
        display: flex;
        flex-direction: row;
        height: fit-content;
        width: 100%;
        justify-content: center;
    }

    svg{
        color: beige;
        border: 2px solid beige;
        padding: 3px;
        border-radius: 4px;
        margin-inline: 4px;
    }

    .opinion{
        width: 100%;
        height: fit-content;
        display: flex;
        justify-content: flex-start;
        align-items: flex-start;
        text-align: start;
        margin-left: 0;
        padding: 10px;
    }

    p{
        color: beige;
    }

</style>