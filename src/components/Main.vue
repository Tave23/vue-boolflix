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
            
            <!-- lingua dinamica -->
            <div v-if="film.original_language === 'it'" class="lingua">
               <p>Lingua: </p><img src="../assets/it.png" alt="Italia" class="img-lingua">
            </div>

            <div v-else-if="film.original_language === 'en'" class="lingua">
               <p>Lingua: </p><img src="../assets/en.png" alt="England" class="img-lingua">
            </div>

            <div v-else>
               <p>Lingua: {{film.original_language}}</p>
            </div>
            <!-- !lingua dinamica -->

            <p>Voto: {{film.vote_average}}</p>
            
         </div>

      </div>

      <div 
      v-if="emptySerie"
      class="serieTv">

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

               <!-- lingua dinamica -->
               <div v-if="serie.original_language === 'it'" class="lingua">
                  <p>Lingua: </p><img src="../assets/it.png" alt="Italia" class="img-lingua">
               </div>

               <div v-else-if="serie.original_language === 'en'" class="lingua">
                  <p>Lingua: </p><img src="../assets/en.png" alt="England" class="img-lingua">
               </div>

               <div v-else>
                  <p>Lingua: {{serie.original_language}}</p>
               </div>
              <!-- !lingua dinamica -->
               <p>Voto: {{serie.vote_average}}</p>
               
            </div>

         </div>
      
      </div>

      <div 
      v-else
      class="emptySerieTv">

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
   data(){
         return{
            // da cambiare in false!!!!!!!!*******+
            emptyFilm: true, 

            emptySerie: true,
         }
   },
   mounted(){

      this.emptyArrayTv

      // emptyArraySerie(){
      //    if (this.researchSeriesMain == '') {
      //       this.emptySerie == true;
      //       console.log(this.emptySerie);
      //    }
      //    return this.emptySerie
      // }
   },
   methods:{
      emptyArrayTv(){
         if (this.researchFilmMain.length === 0) {
            this.emptySerie = true
         }
      },
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
   font-family: 'Trebuchet MS', sans-serif;
}

.container-film{
   display: flex;
   overflow-x: auto;
   width: 90%;
   margin: 0 auto;
   margin-bottom: 70px;
   min-height: 150px;
}

.card-film{
   width: 20%;
   min-height: 300px;
   min-width: 250px;
   border: 1px solid black;
   margin-right: 10px;
   margin-top: 15px;
   margin-bottom: 10px;
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

.lingua{
   display: flex;
   justify-content: center;
}

.img-lingua{
   width: 25px;

}

.card-film,
.title{
   padding: 20px;
   text-align: center;
}
</style>
