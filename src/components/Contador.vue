<template>
    <h2>{{ this.encabezado }} : {{ valor2 }}</h2>

    <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
    <p>{{ this.numero }} <sup>2</sup> = {{ calcularCuadradoComputado }}</p>
    <div>
        <button v-on:click="incrementar">+1</button>
        <button @click="decrementar">-1</button> 
    </div> 

    <div v-if="esVerdad">
        <h1>Feliz Navidad</h1>
    </div>



</template>

<script>
export default {
    data() {
        return {
            numero: this.valor,
            titulo: 'Contador',
        }
    },
    methods: {
        calcularCuadrado() {
            console.log("Entro a calcular")
            return this.numero * this.numero;
        },
        incrementar() {
            this.numero++;
        },
        decrementar() {
            this.numero--;
        }
    },
    computed: {
        calcularCuadradoComputado() {
            console.log("Entro a calcular computado")
            return this.numero * this.numero;
        }
    },

    //props: ['encabezado', 'valor'] //se puede usar como una propiedad reactiva

    props:{
        encabezado:{
            type:String,
            required:false,
            validator(value){
                return !value.includes('a')
                    
                
            }
        },
        valor:Number,
        valor2:{
            type:Number,
            required:false,
            default:777,
            validator(value){
                //programo la validacion bajomi cirterio y retorno
                //true si es valido y false si no es valido
                return value<=1000;
            }
        },
        esVerdad:{
            type:Boolean,
            required:true,
        },
        arreglo:Array,
        fecha:Date,
        objetoPersona:Object,

    }
}
</script>   

<style scoped>
button {
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

button:hover {
    background: #ffba08;
}
</style>
