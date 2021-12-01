<template>
  <div class="header">

    <div class="logo-header">
      <img src="../assets/logo.png" alt="LogoVue">
      <h1>Boolflix</h1>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    
  }
}
</script>

<style scoped lang="scss">

.header{
  height: 80px;
  width: 100vw;
  background-color: black;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}

.logo-header{
  width: 20%;
  display: flex;
  line-height: 80px;
  padding: 10px;
  cursor: pointer;
}

.logo-header img{
  width: 28%;
}

h1{
  color: #F00800;
  padding-left: 20px;
}

</style>
