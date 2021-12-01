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
      userSearch: '',
      listFilms: [],
      listSeries: [],
      keyUrlApi: 'api_key=e99307154c6dfb0b4750f6603256716d',
      defaultUrlFilm: 'https://api.themoviedb.org/3/search/movie?',
      defaultUrlTv: 'https://api.themoviedb.org/3/search/tv?',
      isLoading: false
    }
  },
  methods:{
      getApi(){
      
      // chiamata per i film
      axios.get(`${this.defaultUrlFilm}${this.keyUrlApi}&&query=${this.userSearch}`)
      .then(r =>{
        this.isLoading = true;

        this.listFilms = r.data.results;

        console.log('lista dei film: ',this.listFilms);

        // faccio l'emit per passarlo al padre (app.vue)
        this.$emit('search', this.listFilms);
      })
      .catch( e => {
        console.log(e);
      });

      // seconda chiamata per le serie Tv
      axios.get(`${this.defaultUrlTv}${this.keyUrlApi}&&query=${this.userSearch}`)
      .then(r =>{
        this.isLoading = true;

        this.listSeries = r.data.results;

        console.log('lista delle serie tv: ',this.listSeries);

        // faccio l'emit per passarlo al padre (app.vue)
        this.$emit('searchTv', this.listSeries);
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
