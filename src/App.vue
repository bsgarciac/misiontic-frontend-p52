<template>
  <div id="app">
    <div class="header shadow">
      <h2>Banco Misión TIC</h2>
      <div class="buttons">
        <button v-on:click="loadLogIn" v-if="!is_auth">Ingresar</button>
        <button v-on:click="loadSignUp" v-if="!is_auth">Registro</button>
        <button v-on:click="logout" v-if="is_auth">Cerrar sesión</button>
      </div>
      <div class="menu">
        <img src="./assets/menu.png">
      </div> 
    </div>
    <router-view v-on:completedLogin="completedLogin"></router-view>
  </div>
</template>

<script>
export default {
    name: "App", // Nombre del componente
    data: function() {
      return {
        is_auth: false
      }
    }, // Todas las variables de este componentes
    methods: {
      verifyAuth(){
        this.is_auth = localStorage.getItem("is_auth") || false;
        if(this.is_auth){
          console.log("ir la página de inicio")
        }else{
          this.loadLogIn();
        }
      },  
      loadLogIn(){
        this.$router.push({name: "logIn"});
      },
      loadSignUp(){
        this.$router.push({name: "signUp"});
      },
      completedLogin(data){
        this.is_auth = true;
        localStorage.setItem("is_auth", true);
        localStorage.setItem("token", data.token);
        localStorage.setItem("username", data.username);
      },
      logout(){
        this.is_auth = false;
        localStorage.clear();
      }
    }, // Todas las funciones que usa este componente
    created: function () {
      this.verifyAuth();
    } // Eventos: lo que pasa cuando el componente se inicia
};
</script>

<style>
  .header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #0d0d73;
        color: white;
        padding: 10px 50px;
        height: 54px
  }
  body{
    margin: 0;
  }
  .header h2{
    margin: 0;
    font-family: sans-serif;
  }
  .header button{
    border: none;
    background-color: transparent;
    color: white;
  }
  .menu{
    display: none;
  }
  .menu img{
        width: 25px;
  }
  @media(max-width: 500px){
    .buttons{
      display: none;
    }
    .menu {
      display: block;
    }
    .header{
      padding: 10px 20px;
    }
  }
</style>
