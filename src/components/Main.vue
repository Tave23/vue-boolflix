<template>
  <div class="main">

   <div v-for="film in researchFilmMain"
   :key="film.key"
   class="card-film"> 

      <h4>Titolo: {{film.title}}</h4>
      <p>Titolo originale: {{film.original_title}}</p>
      <p>Lingua: {{film.original_language}}</p>
      <p>Voto: {{film.vote_average}}</p>
      
   </div>

  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
   researchFilmMain: Array
  },
  mounted(){
     
  },
  methods:{
     
  }
}
</script>

<style scoped lang="scss">

.main{
   height: calc(100vh - 80px);
   width: 100vw;
   background: rgb(0,0,0);
   background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(255,10,0,1) 110%);
   overflow-y: scroll;
   padding: 100px 10px;
}

p,
h4{
   color: white;
}

.card-film{
   padding: 20px;
   text-align: center;
}
</style>
