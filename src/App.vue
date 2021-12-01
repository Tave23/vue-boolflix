<template>
  <div id="app">
    
    <Header @search= 'searchFilm'/>
    <Main />

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data(){
    return{

    }
  },

  methods:{
    searchFilm(listFilms){
      console.log('app.vue: ', listFilms);
    }
  }
}
</script>

<style lang="scss">

@import './assets/style/generals.scss';

#app{
  overflow: hidden;
}
</style>
