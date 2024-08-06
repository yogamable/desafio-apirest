<template>
  <div class="p-5 row">
    
    <div class="col d-block">
      <div v-for="(usuario, index) in usuarios" :key="index">
        <img :src="usuario.picture.medium" class="img-thumbnail" />
        <h1>{{ usuario.name }}</h1>
      </div>

      <input type="color" class="form-control form-control-color mt-2" id="exampleColorInput" value="#563d7c" title="Choose your color" v-model="colorElegido">

      <textarea v-model="mensaje" class="form-control mt-2" rows="3"></textarea>

      <button type="button" class="btn btn-light mt-2" @click="enviarMensaje" >Enviar</button>       
    </div>

    <div class="col d-block" :style="{backgroundColor: chatBg}">
      <h2>{{usuario.name }}</h2>
      <div v-for="(mensaje, index) in mensajes" :key="index" >
        <p>{{ mensaje }}</p>

      </div>
    </div> 

    <div class="col d-block">
      <div v-for="(usuario, index) in usuarios" :key="index">
        <img src="usuario.picture.medium" class="img-thumbnail" alt="...">
      </div>
      <h1>{{ name }}</h1>
      <input type="color" class="form-control form-control-color mt-2" id="exampleColorInput" value="#563d7c" title="Choose your color">
      <textarea class="form-control mt-2" id="exampleFormControlTextarea1" rows="3"></textarea>
      <button type="button" class="btn btn-light mt-2">Enviar</button>       
    </div>
   
  </div>
  
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data(){
    return {
      usuarios: [],
      usuario: "",
      colorElegido: "",
      mensaje: "",
      mensajeUsuario: "",
      chatBg: "#E6D3A6",
    }
  },
  methods: {
    async mounted(){
      const url = 'https://randomuser.me/api?results=100';
      const { data } = await axios.get(url);
      this.usuarios = data.results;
      console.log(data.results);
    
    },
    enviarMensaje(){
      
    }

  },

}
</script>

<style>

</style>
