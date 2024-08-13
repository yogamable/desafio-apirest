<template>
    <div>
        <div>
            <img :src="usuario.picture.medium" class="img-thumbnail" />
            <h1 :id="nombre" >{{ usuario.name.first }} {{ usuario.name.last }}</h1>
        </div>
        <form @submit.prevent="enviarMensaje">
            <input type="color" class="form-control form-control-color mt-2 w-100" id="exampleColorInput" v-model="colorElegido">
    
            <textarea v-model="mensajeUsuario" class="form-control mt-2" rows="3"></textarea>
    
            <button class="btn btn-light mt-2" :type="submit" >Enviar</button>       
        </form>
    </div>
</template>

<script>

export default {
    name: 'ProfileComponent',
    data() {
        return {
            nombre: "",
            colorElegido: "#563d7c",
            mensajeUsuario: "",
            posicionUsuario: "",
        }
    },
    props: {usuario: Object},
    methods: {
        enviarMensaje(){

            this.$emit('enviarMensaje', {
                nombre: this.nombre,
                colorElegido: this.colorElegido,
                mensajeUsuario: this.mensajeUsuario,
                posicionUsuario: this.posicionUsuario,
            });

            this.mensajeUsuario = "";

            console.log(this.enviarMensaje);
        },
    }
}

</script>

<style scoped>

</style>