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
               <!-- immagine copertina -->
               <div class="front" :style="{ backgroundImage: `url('${urlBasePoster}${film.poster_path}')` }">
               <!-- // immagine copertina -->
               <div class="content">
                  <!-- titolo nel front se non ho la copertina -->
                  <div
                  class="cover-title"
                  v-if="film.poster_path == null">
                     <h4>{{film.title}}</h4>
                     <p>Copertina non disponibile</p>
                  </div>
                  <div
                  v-else>
                  </div><br>
                  <!-- // titolo nel front se non ho la copertina -->
                  <span class="click-for-more">
                  </span>
               </div>
               </div>
               <div class="back">
               <div class="content">
                  <span class="title">
                     <h2>{{film.title}}</h2>
                  </span>
                  <div class="original-title">
                     <h5>Titolo originale:</h5>
                     <h4>{{film.original_title}}</h4>
                  </div>
                  
                  <!-- lingua dinamica -->
                  <div v-if="flagList.includes(film.original_language)" class="flagLang">
                     <img :src="require(`../assets/${film.original_language}.png`)" alt="Italia" class="img-lingua">
                  </div>

                  <div v-else class="flagLang">
                     <p>Lingua: {{film.original_language}}</p>
                  </div>
                  <!-- !lingua dinamica -->

                  <!-- stelline in base al voto -->
                  <div class="vote">
                     <i 
                     v-for="(star, index) in 5" :key="index"
                     :class="index < Math.round(film.vote_average/2) ? 'fas' : 'far' "
                     class="fa-star"></i>
                  </div>
                  <!-- // stelline in base al voto -->

                  <!-- riassunto programma -->
                  <div class="overview">
                     <p>{{film.overview}}</p>
                  </div>
                  <!-- // riassunto programma -->

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
                  <div
                  class="cover-title"
                  v-if="serie.poster_path == null">
                     <h4>{{serie.name}}</h4>
                     <p>Copertina non disponibile</p>
                  </div>
                  <div
                  v-else>
                  </div><br>
                  <span class="click-for-more">
                  </span>
               </div>
               </div>
               <!-- RETRO CARD -->
               <div class="back">
               <div class="content">
                  <span class="title">
                     <h2>{{serie.name}}</h2>
                  </span>
                  <p class="original-title">
                     Titolo originale: {{serie.original_name}}
                  </p>
                  
                  <!-- lingua dinamica -->
                  <div v-if="flagList.includes(serie.original_language)" class="flagLang">
                     <img :src="require(`../assets/${serie.original_language}.png`)" alt="Italia" class="img-lingua">
                  </div>

                  <div v-else class="flagLang">
                     <p>Lingua: {{serie.original_language}}</p>
                  </div>
                  <!-- !lingua dinamica -->

                  <!-- stelline in base al voto -->
                  <div class="vote">
                     <i 
                     v-for="(star, index) in 5" :key="index"
                     :class="index < Math.round(serie.vote_average/2) ? 'fas' : 'far' "
                     class="fa-star"></i>
                  </div>
                  <!-- // stelline in base al voto -->

                  <!-- riassunto programma -->
                  <div class="overview">
                     <p>{{serie.overview}}</p>
                  </div>
                  <!-- // riassunto programma -->

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
         // array delle flag che ho
         flagList:['en', 'it'],

         urlBasePoster: 'https://image.tmdb.org/t/p/w342'
      }
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
   max-width: 250px;
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

.flagLang{
   display: flex;
}

.flagLang img{
   margin-left: 5px
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
   text-align: left;
}

.original-title{
   padding-bottom: 10px;
}

.cover-title{
   display: flex;
   justify-content: space-between;
   flex-direction: column;
   height: 100%;
}

.cover-title p{
   font-size: 12px;
}

.vote{
   margin-top: 5px;
}

.fas{
   color: yellow;
}

.overview{
   height: fit-content;
   overflow-y: scroll;
   padding: 10px 0 5px;
   font-size: 12px;
   margin-top: 5px;
}

// ********
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
  align-content: left;
  min-height: 300px;
  min-width: 240px;
  flex-wrap: wrap;
  position: relative;
  border: 7px solid transparent;
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
    justify-content: left;
    padding: 5px 10px;
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
      border: 7px solid transparent;
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
      border: 7px solid transparent;
      border-bottom:7px solid white;
      border-right:7px solid white;
    }
  }
  
  .content {
    display: flex;
    justify-content: left;
    align-items: left;
    flex-direction: column;
    text-shadow: 0px 0px 2px black;
  
  }

  .content .title{
     margin-bottom: 15px;
     text-align: left;
  }
}
</style>
