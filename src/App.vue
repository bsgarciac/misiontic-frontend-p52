<template>
  <div id="app">
    <div class="header shadow">
      <h2>Banco Misión TIC</h2>
      <div class="buttons">
        <button>Ingresar</button>
        <button>Registro</button>
      </div>
      <div class="menu">
        <img src="./assets/menu.png">
      </div> 
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
    name: "App", // Nombre del componente
    data: function() {}, // Todas las variables de este componentes
    methods: {
      loadLogIn(){
        this.$router.push({name: "logIn"});
      }
    }, // Todas las funciones que usa este componente
    created: function () {
      this.loadLogIn();
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
