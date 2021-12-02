<template>
   <div class="main">

      <div class="categories">
         <h2>Film</h2>
      </div>

      <div class="container-film">
         <div class="row flip-boxes">
            <div 
            v-for="film in researchFilmMain"
            :key="film.key"
            class="col-md-3 col-sm-4 col-8 flip-box">
               <div class="front" :style="{ backgroundImage: `url('${urlBasePoster}${film.poster_path}')` }">
               <div class="content">
                  <br>
                  <span class="click-for-more">
                  </span>
               </div>
               </div>
               <div class="back">
               <div class="content">
                  <span class="title">
                     <p>Titolo: </p>
                     <h2>{{film.title}}</h2>
                  </span>
                  <p class="original-title">
                     Titolo originale: {{film.original_title}}
                  </p>
                  
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
            </div>
         </div>
      </div>

      <div class="categories">
         <h2>Serie TV</h2>
      </div>

      <!-- CONTAINER SERIE TV -->
      <div class="container-film">
         <div class="row flip-boxes">
            <div 
            v-for="serie in researchSeriesMain"
            :key="serie.key"
            class="col-md-3 col-sm-4 col-8 flip-box">
               <!-- FRONTE CARD -->
               <div class="front" :style="{ backgroundImage: `url('${urlBasePoster}${serie.poster_path}')` }">
               <div class="content">
                  <br>
                  <span class="click-for-more">
                  </span>
               </div>
               </div>
               <!-- RETRO CARD -->
               <div class="back">
               <div class="content">
                  <span class="title">
                     <p>Titolo: </p>
                     <h2>{{serie.name}}</h2>
                  </span>
                  <p class="original-title">
                     Titolo originale: {{serie.original_name}}
                  </p>
                  
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
         </div>
      </div>
      <!-- //CONTAINER SERIE TV -->

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

         urlBasePoster: 'https://image.tmdb.org/t/p/w342'
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
   background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(255,10,0,1) 100%);
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
   background-color: rgb(59, 2, 0);
}

.categories{
   width: 90%;
   margin: 0 auto;
   margin-bottom: 20px;
}

p,
h4,
h2{
   color: white;
}

.lingua{
   display: flex;
   justify-content: left;
   align-items: center;
   padding-bottom: 10px;
}

.img-lingua{
   width: 20px;
   height: 15px;
}

.card-film,
.title{
   padding: 0 20px;
   text-align: left;
}

.original-title{
   padding-bottom: 10px;
}


// flipcard
body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
.flip-boxes {
  justify-content: center;
  display: flex;
}
.flip-box {
  display: flex;
  align-content: stretch;
  min-height: 300px;
  min-width: 240px;
  flex-wrap: wrap;
  position: relative;
  border: 10px solid transparent;
  padding:0;
  border-top: 0;  
  -webkit-perspective: 1000;
          perspective: 1000;
  
  &:hover {
    .back {
      transform: rotateY(0deg);
      z-index: 10;
    }
    
    .front {
      transform: rotateY(180deg);
      z-index: -1;
    }
    
  }
  
  .back, .front {
    position: relative;
    background-color: #1b2d61;
    color: white;
    display: flex;
    justify-content: center;
    align-content: center;
    flex: 0 0 100%;
    -webkit-transition: all 1.5s cubic-bezier(.5,1,.5,1);
    transition: all 1.5s cubic-bezier(.5,1.3,.5,1.3);
    transform-style: preserve-3d;
    background-size: cover;
    background-position: center;
  }
  
  .back {
    background-color: rgb(59, 2, 0);
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 100%;
    z-index: -1;
    transform: rotateY(-180deg);
    
    &:after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      width: 30px;
      height: 30px;
      border: 15px solid transparent;
      border-bottom-color: white;
      border-left-color: white;
    }
  }
  
  .front {
    z-index: 10;
    
    .content {
      font-size: 2rem;
    }
    
    &:after {
      content: "";
      position: absolute;
      bottom: 0;
      right: 0;
      width: 30px;
      height: 30px;
      border: 15px solid transparent;
      border-bottom:10px solid white;
      border-right:10px solid white;
    }
  }
  
  .content {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    -webkit-transform: translateZ(50px);
            transform: translateZ(50px);
    text-shadow: 0px 0px 2px black;
  
  }
}
</style>
