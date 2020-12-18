<template>
    <div id="UserCount">
        <h2>{{username}}</h2>
        <h2>Tus datos son: <span> {{count}} . </span> </h2>
    </div>
</template>


<script>
import axios from 'axios';
export default {
    name: 'UserCount',
    data: function (){
        return {
            username: "",
            count: ""
        }
    },
    created: function(){
        this.username = this.$route.params.username
        let self = this
        axios.get("https://hotel-app-ciclo3.herokuapp.com/user/count/" + this.username)
            .then((result) => {
                console.log("objetos %0:",result.data);
                self.count = result.data.username
            })
            .catch((error) => {
            alert("ERROR Servidor");
            });
    }
}
</script>


<style>
    #UserCount{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    #UserCount h2{
        font-size: 50px;
        color: #283747;
    }
    #UserCount span{
        color: crimson;
        font-weight: bold;
    }
</style>
