<template>
    <div>
        <div class="background"></div>

        <div class="form shadow-lg ">
            <h3>Iniciar Sesión</h3>
            <form>
                <input class="form-control" placeholder="Usuario"/>
                <input class="form-control" type="password" placeholder="Contraseña"/> 
                <button class="btn btn-primary">Ingresar</button>
            </form>
        </div>
    </div>
</template>


<script>
export default {
    name: "LogIn", // Nombre del componente
    data: function() {}, // Todas las variables de este componentes
    methods: {}, // Todas las funciones que usa este componente
    created: function () {} // Eventos: lo que pasa cuando el componente se inicia
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
</style>