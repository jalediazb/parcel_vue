<template>
  <section id="main" class="section has-background-light">
    <div class="container">
      <div class="box">
        <h1 class="title is-size-2 is-size-4-touch has-text-centered">
          {{ message }}
        </h1>
        <hr>
        <p class="has-text-centered">
          <Boton :text="btnText" color="is-warning"></Boton>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
import Boton from "./components/Boton.vue"
export default {
  name: "App",
  components: {Boton},
  data() {
    return {
      message: "Proyecto Vue y Parcel",
      btnText: "Componente",
    };
  },
};
</script>

<style>
#main {
  min-height: 100vh;
}
</style>