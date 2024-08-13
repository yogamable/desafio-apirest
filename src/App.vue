<template>
  <div id="app" class="d-flex p-5 row">
    <div class="col d-block">
      <ProfileComponent v-if="usuarios.length"
      :usuario="usuarios[0]"
      @enviarMensaje="recibirMensaje($event,0)"
      />

    </div>
    
    <div data-bs-spy="scroll" class="col rounded-4" :style="{backgroundColor: chatBg}">
      <div class="row d-block">
        <ChatComponent 
        :mensajes="chatMensajes"
        />
        
      </div>

    </div>

    <div class="col d-flex">
      <ProfileComponent v-if="usuarios.length"
      :usuario="usuarios[1]"
      @enviarMensaje="recibirMensaje($event,1)"
      />

    </div>
    
   
  </div>
  
</template>

<script>
import axios from 'axios';
import ProfileComponent from './components/ProfileComponent.vue';
import ChatComponent from './components/ChatComponent.vue';

export default {
  name: 'App',
  data(){
    return {
      usuarios: [],
      chatMensajes: [],
      chatBg: "#E6D3A6",
      posicionUsuarios: [],
      textAlign: 'right',
    }
  },
  async mounted(){
    const url = 'https://randomuser.me/api?results=2';
    const { data } = await axios.get(url);
    this.usuarios = data.results;
    console.log(this.usuarios);
  },
  components: {
    ProfileComponent,
    ChatComponent,
    
  },
  methods: {
    recibirMensaje(mensaje, posicionUsuario){

      //this.chatMensajes.push(mensaje);
      let posicion = posicionUsuario === 0 ? 0 : 1 ;
      
      let nuevoMensaje = {
        nombre: this.usuarios[posicion].name.first,
        colorElegido: mensaje.colorElegido || "#fffff",
        mensajeUsuario: mensaje.mensajeUsuario,
        posicionUsuario: posicion,
      }
      this.chatMensajes.push(nuevoMensaje);

    },

  },

}
</script>

<style>

</style>
