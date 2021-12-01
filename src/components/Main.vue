<template>
  <div class="main">

     <p>{{researchFilmMain}}</p>

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
   background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(255,10,0,1) 100%);
   overflow-y: scroll;
}

</style>
