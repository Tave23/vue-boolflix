<template>
   <div class="main">

      <div class="categories">
         <h2>Film</h2>
      </div>

      <div class="container-film">

         <div v-for="film in researchFilmMain"
         :key="film.key"
         class="card-film"> 

            <span class="title">
               <p>Titolo: </p>
               <h2>{{film.title}}</h2>
            </span>
            <p>Titolo originale: {{film.original_title}}</p>
            <p>Lingua: {{film.original_language}}</p>
            <p>Voto: {{film.vote_average}}</p>
            
         </div>

      </div>

      <div class="categories">
         <h2>Serie TV</h2>
      </div>

      <div class="container-film">

         <div v-for="serie in researchSeriesMain"
         :key="serie.key"
         class="card-film"> 

            <span class="title">
               <p>Titolo: </p>
               <h2>{{serie.name}}</h2>
            </span>
            <p>Titolo originale: {{serie.original_name}}</p>
            <p>Lingua: {{serie.original_language}}</p>
            <p>Voto: {{serie.vote_average}}</p>
            
         </div>

      </div>

   </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
   // array film
   researchFilmMain: Array,
   // array serieTv
   researchSeriesMain: Array
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
   padding: 80px 10px;
   font-family: 'Trebuchet MS', sans-serif;
}

.container-film{
   display: flex;
   overflow-x: scroll;
   width: 90%;
   margin: 0 auto;
   margin-bottom: 70px;
   min-height: 150px;
}

.card-film{
   width: 20%;
   min-width: 250px;
}

.categories{
   width: 90%;
   margin: 0 auto;
}

p,
h4,
h2{
   color: white;
}

.card-film,
.title{
   padding: 20px;
   text-align: center;
}
</style>
