<template>
  <div id="app">
    
    <Header @search= 'searchFilm'/>
    <Main :researchFilmMain='listFilms2'/>

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
      listFilms2: []
    }
  },

  methods:{
    searchFilm(listFilms){
      console.log('app.vue ', listFilms);

      this.listFilms2 = listFilms
      console.log('nuovo array dentro app.vue ',this.listFilms2);
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
