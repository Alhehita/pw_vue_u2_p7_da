<template>
    <img :src="imagen" alt="No se puede mostrar la imagen">

    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
    <p>Recuerda que cuando finalices tu pregunta da un enter</p>

    <h1>{{ pregunta }}</h1>
    <h2>{{respuesta}}</h2>

</template>


<script>
export default {
    data() {
        return {
            pregunta: 'Hola mundo',
            respuesta: null,
            imagen:"https://yesno.wtf/assets/no/3-80a6f5b5d6684674bcfeda34accca4e1.gif"
        }
    },
    watch: {
        pregunta(value, oldValue) {
            console.log(value);
            console.log(oldValue);
            if (value.includes('?')) {
                //programar la respuesta
                console.log('aqui llamo a la api');
                this.llamarAPI();
            }
        }
    },
    methods: {
        async llamarAPI() {
          const data = await fetch('https://yesno.wtf/api').then(resp=>resp.json())
          this.respuesta = data.answer;  
          this.imagen = data.image; 
          console.log(data);
        }
    }
}
</script>

<style></style>