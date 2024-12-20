<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <contador encabezado="Contador" :valor="calcular(1, 3)" :esVerdad="muestra1" :valor2="8" />
  <contador encabezado="Segundo" :valor="5 + 3" :esVerdad="muestra2" />
  <button @click="cambiar(1)">Cambiar </button>
  <button @:click="cambiar(2)">Cambiar Segundo</button>
</template>

<script>
import contador from './components/Contador.vue'

export default {
  name: 'App',
  components: {
    contador
  },
  data() {
    return {
      muestra: true,
      muestra1: true,
      muestra2: true,
    }
  },
  methods: {
    calcular(a, b) {
      return a + b;
    },

    cambiar(valor) {
      if (valor === 1) {
        this.muestra1 = !this.muestra1;
      } else {
        this.muestra2 = !this.muestra2;

      }
      this.muestra = !this.muestra;
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
