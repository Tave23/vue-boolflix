<template>
  <div class="header">

    <div class="logo-header">
      <img src="../assets/logo.png" alt="LogoVue">
      <h1>Boolflix</h1>
    </div>

    <div class="input-header">
      <input class="form-control" type="text" placeholder="Inserisci il nome di un film...">
      <button type="button" class="button-input">Cerca</button>
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
  color: #F00800;
  padding-left: 20px;
  cursor: pointer;
}

.button-input{
  background-color: #F00800;
  border: none;
  padding: 5px;
  color: white;
  margin-left: 10px;
}

.button-input:active{
  background-color: #b40802;
}
</style>
