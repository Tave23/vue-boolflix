<template>
  <div class="header">

    <div class="logo-header">
      <img src="../assets/logo.png" alt="LogoVue">
      <h1>Boolflix</h1>
    </div>

    <div class="input-header">
      <!-- input title film -->
      <input 
      v-model="userSearch"
      class="form-control" 
      @keyup.enter="getApi"
      type="text" placeholder="Inserisci il nome di un film...">
      <!-- button -->
      <button 
      @click="getApi"
      type="button" 
      class="button-input">Cerca</button>
    </div>

  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'Header',
  props: {
    
  },
  data(){
    return{
      // ciò che cerca l'utente
      userSearch: '',

      // array in cui andranno i risultati della ricerca
      listFilms: [],
      listSeries: [],

      // api Key personale
      keyUrlApi: 'api_key=e99307154c6dfb0b4750f6603256716d',

      // due pezzi BASE dei link per la ricerca
      defaultUrlFilm: 'https://api.themoviedb.org/3/search/movie?',
      defaultUrlTv: 'https://api.themoviedb.org/3/search/tv?',

      // due link per la ricerca di film/serie popolari
      urlResearchBaseFilm: 'https://api.themoviedb.org/3/movie/popular?api_key=7a832fe130a8b7a500ccbe8608c29904&language=en-US&page=1',
      urlResearchBaseSerie: 'https://api.themoviedb.org/3/tv/popular?api_key=7a832fe130a8b7a500ccbe8608c29904&language=en-US&page=1',

    }
  },
  mounted(){
    this.defaultPopular();
  },
  methods:{
    // *************
    // funzione di default prima della ricerca dell'utente
    // *************
      defaultPopular(){

        // chiamata per i film
        axios.get(`${this.urlResearchBaseFilm}`)
        .then(r =>{

          this.listFilms = r.data.results;

          // console.log('lista dei film: ',this.listFilms);

          // faccio l'emit per passarlo al padre (app.vue)
          this.$emit('search', this.listFilms);

          // *******
          this.isLoadingFilm = true;

          this.$emit('loadingFilm', this.isLoadingFilm);
        })
        .catch( e => {
          console.log('errore!',e);
        });

        // seconda chiamata per le serie Tv
        axios.get(`${this.urlResearchBaseSerie}`)
        .then(r =>{

          this.listSeries = r.data.results;

          // console.log('lista delle serie tv: ',this.listSeries);

          // faccio l'emit per passarlo al padre (app.vue)
          this.$emit('searchTv', this.listSeries);

          // *******
          this.isLoadingSerie = true;

          this.$emit('loadingTv', this.isLoadingSerie);
        })
        .catch( e => {
          console.log(e);
        });

      },


    // funzione quando si preme invio o si clicca sul button
      getApi(){
      
      // chiamata per i film
      axios.get(`${this.defaultUrlFilm}${this.keyUrlApi}&query=${this.userSearch}`)
      .then(r =>{

        this.listFilms = r.data.results;

        // console.log('lista dei film: ',this.listFilms);

        // faccio l'emit per passarlo al padre (app.vue)
        this.$emit('search', this.listFilms);

         // *******
        this.isLoadingFilm = true;

        this.$emit('loadingFilm', this.isLoadingFilm);
      })
      .catch( e => {
        console.log('errore!',e);
      });

      // seconda chiamata per le serie Tv
      axios.get(`${this.defaultUrlTv}${this.keyUrlApi}&query=${this.userSearch}`)
      .then(r =>{

        this.listSeries = r.data.results;

        // console.log('lista delle serie tv: ',this.listSeries);

        // faccio l'emit per passarlo al padre (app.vue)
        this.$emit('searchTv', this.listSeries);

        // *******
        this.isLoadingSerie = true;

        this.$emit('loadingTv', this.isLoadingSerie);
      })
      .catch( e => {
        console.log(e);
      });
    },
    
  }
}


</script>


<style scoped lang="scss">

@import '../assets/style/vars.scss';

.header{
  height: 80px;
  width: 100vw;
  background-color: black;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo-header,
.input-header{
  width: 20%;
  display: flex;
  line-height: 80px;
  padding: 10px;
}

.logo-header img{
  width: 28%;
  cursor: pointer;
}

h1{
  color: $button-bg-color;
  padding-left: 20px;
  cursor: pointer;
}

h3{
  color: white;
}

.button-input{
  background-color: $button-bg-color;
  border: none;
  padding: 5px;
  color: white;
  margin-left: 10px;
}

.button-input:active,
.button-input:hover{
  background-color: $active-btn;
}
</style>
