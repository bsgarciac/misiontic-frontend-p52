<template>
  <div id="app">
    <div class="header shadow">
      <h2>Banco Misión TIC</h2>
      <div>
        <button>Ingresar</button>
        <button>Registro</button>
      </div>
    </div>
  </div>
</template>

<style>
  .header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #0d0d73;
        color: white;
        padding: 10px 50px;
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
</style>
