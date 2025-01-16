<template>
    <img :src="imagen" alt="No se puede mostrar la imagen">

    <div class="contenido">
        <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
        <p>Recuerda que cuando finalices tu pregunta da un enter</p>

        <h1>{{ pregunta }}</h1>
        <h2>{{ respuesta }}</h2>
    </div>


</template>


<script>
export default {
    data() {
        return {
            pregunta: 'Preguntame algo',
            respuesta: null,
            imagen: "https://yesno.wtf/assets/no/3-80a6f5b5d6684674bcfeda34accca4e1.gif"
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
            const data = await fetch('https://yesno.wtf/api').then(resp => resp.json())
            this.respuesta = data.answer;
            this.imagen = data.image;
            console.log(data);
        }
    }
}
</script>

<style scoped>
img {
    max-height: 100%;
    height: 100vh;
    max-width: 100%;
    width: 100vw;
    position: fixed;
    top: 0px;
    left: 0px;
}

.contenido {
    position: relative;
    top: 0px;
    left: 0px;
    width: 100vw;
    height: 100vh;
    text-align: center ;
    justify-content: center;
    font-size:30px;
    
}

input {
margin-top: 25%;
width: 260px;
padding: 15px 30px;
border: none;
border-radius: 7px;
font-size: 18px;
}

h1,h2,p{
    color: white;
    text-align: center;
}
</style>