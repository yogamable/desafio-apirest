<template>
  <div v-for="mensaje in mensajes" :key="mensaje">
    <div class="p-3 row w-100 d-flex" :style="{justifyContent: mensaje.posicionUsuario === 1 ? 'start' : 'end', textAlign: mensaje.posicionUsuario === 1 ? 'end' : 'start'}">
      <h2 class="fs-6" >{{ mensaje.nombre }}</h2>
      <p class="rounded" :style="{backgroundColor: mensaje.colorElegido, color: getContrastingColor(mensaje.colorElegido)}">{{ mensaje.mensajeUsuario }}</p>
    </div>
  </div>   
</template>

<script>
export default {
    name: 'ChatComponent',
       
    props: {
      mensajes: Array
    },

    methods: {
      getContrastingColor(hexColor) {
      const rgb = this.hexToRgb(hexColor);
      const brightness = (rgb.r * 299 + rgb.g * 587 + rgb.b * 114) / 1000;
      return brightness > 128 ? '#000000' : '#ffffff';
    },
    // Convertir HEX a RGB
    hexToRgb(hex) {
      let shorthandRegex = /^#?([a-f\d])([a-f\d])([a-f\d])$/i;
      hex = hex.replace(shorthandRegex, function(m, r, g, b) {
        return r + r + g + g + b + b;
      });

      let result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
      return result ? {
        r: parseInt(result[1], 16),
        g: parseInt(result[2], 16),
        b: parseInt(result[3], 16)
      } : null;
    }
    }
}

</script>

<style scoped>

</style>