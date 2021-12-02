<template>
    <div>
        <div class="background"></div>

        <div class="form shadow-lg ">
            <h3>Iniciar Sesión</h3>
            <form v-on:submit.prevent="processLogIn">
                <input v-model="credentials.username" class="form-control" placeholder="Usuario"/>
                <input v-model="credentials.password" class="form-control" type="password" placeholder="Contraseña"/> 
                <button class="btn btn-primary">Ingresar</button>
            </form>
        </div>
    </div>
</template>


<script>
import gql from "graphql-tag";

export default {
    name: "LogIn", 
    data: function() {
        return {
            credentials: {
                username: "",
                password: ""
            }
        }
    }, 
    methods: {
        processLogIn: async function (){
            await this.$apollo.mutate({
                mutation: gql`
                    mutation Login($credentials: LoginInput!) {
                        login(credentials: $credentials) {
                            key
                        }
                    }
                `,
                variables: {
                    credentials: this.credentials
                }
            })
            .then((result) => {
                console.log("FUNCIONÓOOO")
                console.log(result)
            })
            .catch((error)=>{
                console.log("DIO ERROR :c")
                console.log(error)
            })
        }
    }, 
    created: function () {}
};
</script>


<style >
    .background{
        background-image: url("https://images.pexels.com/photos/351264/pexels-photo-351264.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940");
        height: calc(100vh - 54px);
    }
    .form{
        position: absolute;
        top: 50%;
        left: 50%;
        background-color: white;
        transform: translate(-50%, -50%);
        padding: 80px 50px;
        border-radius: 10px;
    }
    .form form{
        display: flex;
    flex-direction: column;
    }
    .form input{
        margin-bottom: 25px;
    }
    .form h3{
        text-align: center;
        margin-bottom: 30px;
    }

    @media(max-width: 500px){
        .form {
             padding: 40px 25px;
            width: 85%;
        }
    }
</style>