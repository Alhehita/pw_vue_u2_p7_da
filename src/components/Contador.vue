<template>
  <h2>{{titulo}}</h2>
  
  <p>{{ numero }} <sup>2</sup> = {{calcularCuadradoComputado}}</p>
  <p>{{ numero }} <sup>2</sup> = {{calcularCuadradoComputado}}</p>
  <div>
    <button v-on:click="incrementar">+1</button>
    <button v-on:click="decrementar">-1</button>
  </div>
  


</template>

<script>
export default {
    data(){
        return{
            numero:17,
            titulo:'Contador',
        }
    },
    methods:{
        calcularCuadrado(){
            console.log("Entro a calcular")
            return this.numero*this.numero;
        },
        incrementar(){
            this.numero++;
        },
        decrementar(){
            this.numero--;
        }
    },
    computed:{
        calcularCuadradoComputado(){
            console.log("Entro a calcular computado")
            return this.numero*this.numero;
        }
    }
}
</script>

<style scoped>

button{
    padding: 5px;
    border: solid 1px #ee9b00;
    border-radius: 5px;
    margin: 5px;
    width: 40px;
    background: #ca6702;
    color: #370617;
    cursor: pointer;
    font-style: bold;
}

button:hover{
    background: #ffba08;
}
</style>

