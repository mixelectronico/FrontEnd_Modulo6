<template>
    <div id="NotFound">
        <div id="message" class="alert alert-warning" role="alert">
            La página que quieres acceder no existe<br>¡Lo sentimos!
        </div>
    </div>
</template>

<script>
export default{
    name: 'NotFound',
    //props: {},
    data: function(){
        return{}
    },
    //computed: {},
    //methods: {},
    //watch: {},
    //components: {},
    //mixins: [],
    //filters: {},
    //-- LifeCycle Methods
    //-- End LifeCycle Methods
}
</script>

<style scoped>
    #NotFound{
        width: 100%;
        display: flex;
        justify-content: center;
    }

    #message{
        margin-top: 100px;
        width: fit-content;
    }
</style>