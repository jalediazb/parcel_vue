<template>
  <button :class="color" class="button" @click="mensaje()">{{ text }}</button>
</template>
<script>
export default {
  name: "Boton",
  props: ['color', 'text'],
  data: function () {
    return {
      textoMensaje: "Hola",
    }
  },
  methods: {
    mensaje: function() {
      alert(this.textoMensaje)
    }
  }
}
</script>
