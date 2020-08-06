<template>
     <div class="container">
        <h1>Busca una película</h1>
        <b-form-input v-model="text" placeholder="Buscar película" v-on:keyup.enter="getMovie"></b-form-input>
        <button v-on:click="getMovie">Buscar película</button>

        <!-- UTILIZAR V-SHOW PARA OCULTAR PELICULA MIENTRAS LA DATA ESTÉ VACÍA -->
        <div id="ficha" class="container-movie" v-if="!isHidden">
          <div class="container-poster" >
            <img :src="info.data.Poster" />
          </div>

          <div class="container-info">
            <h1>{{ info.data.Title }}<span>({{ info.data.Year }})</span><span id="rating"> <b-icon-star-fill variant="warning"></b-icon-star-fill> {{ info.data.imdbRating }} </span></h1>
            <p>Genero: {{ info.data.Genre }}</p>
            <p>Año: {{ info.data.Year }}</p>
            <p>País: {{ info.data.Country }}</p>
            <p>Duración: {{ info.data.Runtime }}</p> 
            <p>Dirección: {{ info.data.Director }}</p>
            <p>Actores: {{ info.data.Actors }}</p>
            <p>Argumento:{{ info.data.Plot}}</p>

            <button><a :href="`https://www.imdb.com/title/${info.data.imdbID}`">Ver en Imdb </a></button>
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
        info: '',
        ficha: '',
        isHidden: true
      }
    },

    methods: {

    getMovie(){
     axios
    //  .get('http://www.omdbapi.com/?t=joker&apikey=c70674e5')
      .get('http://www.omdbapi.com/?t=' + this.text + '&apikey=c70674e5')
      .then(response => (this.info = response))
      this.isHidden = false;
     
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
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 90%;
    background-color: white;

    h1{
        color: #010101;
        font-size: 26px;
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
        background-color: #010101;
        color: white;
        font-size: 16px;
        border: none;
        padding: 10px 15px;
        margin-top: 25px;
    }

    .container-movie{
      display: flex;
      flex-direction: column;
      margin-top: 10px;
      max-width: 95%;
     

      .container-poster{
         max-width: 500px;

        img{
          height: 500px;
          width: auto;
        }
      }

      .container-info{
        background-color: #313131;
        padding: 20px 15px 30px 30px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-end;
        max-width: 500px;

        h1{
          text-align: left;
          color: #f1f1f1;

          span{
            font-size: 25px;
            margin-left: 15px;
          }

          #rating{
            font-size: 20px;
            text-align: left;
            color: #f1f1f1;
          }
        }

        button{
          background-color: yellow;
          color: #000;

          a{
            color: #000;
            font-weight: 700;
            text-decoration: none;
          }
        }

      }
    }
}

@media only screen and (min-width: 700px)  {


.container{
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 1000px;

    h1{
        color: #010101;
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
        background-color: #010101;
        color: white;
        font-size: 18px;
        border: none;
        padding: 10px 15px;
        margin-top: 25px;
    }

    .container-movie{
      display: flex;
      flex-direction: row;
      margin-top: 100px;

      .container-poster{
    
        img{
          height: 700px;
          width: auto;
        }
      }

      .container-info{
        background-color: #313131;
        padding: 20px 15px 30px 30px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-end;
        max-width: 500px;

        h1{
          text-align: left;
          color: #f1f1f1;
        }

        p{
          font-size: 16px;
          text-align: left;
          color: #f1f1f1;
        }
      }
    }
}
}
</style>




