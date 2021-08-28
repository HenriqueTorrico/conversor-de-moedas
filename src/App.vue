<template>
  <div id="app">
    <h1>Conversor de Moedas</h1>
    <div class="container">
      <div class="conversores"><Conversor moedaA="USD" moedaB="BRL"/></div>
      <div class="conversores"><Conversor moedaA="BRL" moedaB="USD"/></div>
      <div class="conversores"><Conversor moedaA="CAD" moedaB="BRL" /></div>
      <div class="conversores"><Conversor moedaA="BRL" moedaB="CAD" /></div>
      <div class="conversores"><Conversor moedaA="EUR" moedaB="BRL" /></div>
      <div class="conversores"><Conversor moedaA="BRL" moedaB="EUR" /></div>
    </div>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue"

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
  #app {
    max-width: 900px;
    margin: auto;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  #app h1 {
    font-size: 36px;
  }

  .container {
    display: flex;
    max-width: 900px;
    justify-content: space-around;
    flex-wrap: wrap;
  }

  .conversores {
    margin-top: 20px;
  }

  @media(max-width: 816px) {
    .container {
      flex-direction: column;
      align-items: center;
    }

    .conversores {
      margin-bottom: 2px;
    }
  }

  @media(max-width: 320px){
    .container{
      margin: 0 auto;
      display: flex;
      align-items: center;
    }

    .conversores{
      width: 270px;
    }
  }
</style>