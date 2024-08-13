<template>
  <div v-for="mensaje in mensajes" :key="mensaje" class="d-block">
    <div class="m-2 ">
      <h2 class="fs-6" :style="{textAlign: mensaje.posicionUsuario === 1 ? 'right' : 'left'}">{{ mensaje.nombre }}</h2>
    </div>    
    <div>
      <p class="m-2 p-1 ps-2 pe-2 rounded text-center" :style="{backgroundColor: mensaje.colorElegido, textAlign: mensaje.posicionUsuario === 1 ? 'right' : 'left'}">{{ mensaje.mensajeUsuario }}</p>
    </div>
  </div>   
</template>

<script>
export default {
    name: 'ChatComponent',
       
    props: {
      mensajes: Array
    }
}

</script>

<style scoped>

</style>