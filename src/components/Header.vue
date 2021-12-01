<template>
  <div class="header">

    <div class="logo-header">
      <img src="../assets/logo.png" alt="LogoVue">
      <h1>Boolflix</h1>
    </div>

    <div class="input-header">
      <!-- input title film -->
      <input 
      v-model="userFilm"
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
      userFilm: '',
      listFilms: [],
      keyUrlApi: 'api_key=e99307154c6dfb0b4750f6603256716d',
    }
  },
  methods:{
      getApi(){

      axios.get(`https://api.themoviedb.org/3/search/movie?${this.keyUrlApi}&query=${this.userFilm}`)
      .then(r =>{
        this.isLoading = true;

        alert('ho cliccato');

        this.listFilms = r.data.results;

        // console.log(this.listFilms);

        // faccio l'emit per passarlo al padre (app.vue)
        this.$emit('search', this.listFilms)
      })
      .catch( e => {
        console.log(e);
      })
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
