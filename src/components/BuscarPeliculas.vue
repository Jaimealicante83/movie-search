<template>
     <div class="container">
        <h1>Busca una película</h1>
        <b-form-input v-model="text" placeholder="Buscar película" v-on:keyup.enter="getMovie"></b-form-input>
        <button v-on:click="getMovie">Buscar película</button>

        <!-- UTILIZAR V-SHOW PARA OCULTAR PELICULA MIENTRAS LA DATA ESTÉ VACÍA -->
        <div class="container-movie">
          <div class="container-poster">
            <img :src="info.data.Poster" />
          </div>

          <div class="container-info">
            <h1>{{ info.data.Title }}</h1>
            <p>Genero: {{ info.data.Genre }}</p>
            <p>Año: {{ info.data.Year }}</p>
            <p>País: {{ info.data.Country }}</p>
            <p>Duración: {{ info.data.Runtime }}</p> 
            <p>Dirección: {{ info.data.Director }}</p>
            <p>Actores: {{ info.data.Actors }}</p>
            <p>Argumento:{{ info.data.Plot}}</p>
          </div>
        </div>



       <!-- <div class="mt-2">Value: {{ text }}</div>
       <h1> {{ info.data.Title }}</h1>
        <img :src="info.data.Poster" />
        <p>Genero: {{ info.data.Genre }}</p>
        <p>Año: {{ info.data.Year }}</p>
        <p>País: {{ info.data.Country }}</p>
        <p>Duración: {{ info.data.Runtime }}</p> 
        <p>Dirección: {{ info.data.Director }}</p>
        <p>Actores: {{ info.data.Actors }}</p>
        <h1>Titulo {{ info.data.Title }}</h1> -->
        
  </div>

</template>

<script>
import axios from 'axios'
export default {
    name: 'BuscarPeliculas',
     data() {
      return {
        text: '',
        info: ''
      }
    },

    methods: {

    getMovie(){
     axios
    //  .get('http://www.omdbapi.com/?t=joker&apikey=c70674e5')
      .get('http://www.omdbapi.com/?t=' + this.text + '&apikey=c70674e5')
      .then(response => (this.info = response))
     
     }
    
  },

  mounted () {
    axios
    //  .get('http://www.omdbapi.com/?t=joker&apikey=c70674e5')
    .get('http://www.omdbapi.com/?t=' + this.text + '&apikey=c70674e5')
      .then(response => (this.info = response))
  }
}
</script>

<style scoped lang="scss">

.container{
  /*  display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start; */

    h1{
        color: darkblue;
        font-size: 43px;
    }

    img{
        height: 600px;
        width: auto;
    }
    p{
        font-size: 16px;
        font-weight: 200;
        margin: 10px 0;
        color: #000;
    }

    button{
        background-color: darkblue;
        color: white;
        font-size: 14px;
        border: none;
        padding: 10px 15px;
        margin-top: 25px;
    }

    .container-movie{
      display: flex;
      margin-top: 100px;

      .container-poster{

        img{
          height: 700px;
          width: auto;
        }
      }

      .container-info{
        background-color: beige;
        padding: 20px 15px 30px 30px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-end;
        max-width: 500px;

        p{
          font-size: 16px;
          text-align: left;
        }
      }
    }
}
</style>




