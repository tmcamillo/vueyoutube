<template>
  <div id="app">
    <h1>Guia Clientes</h1>
    <input type="text" v-model="clienteMichael.nome" />
    <input type="text" v-model="clienteMichael.email" />
    <Cliente :cliente="clienteMichael" />
    <Cliente nome="Pam" email="email@email.com" idade="56" />
    <Cliente nome="Dwigth" email="email@email.com" idade="10" />
  </div>
</template>

<script>
import Cliente from "./components/Cliente";
// import Produto from "./components/Produto";

export default {
  name: "App",
  data() {
    return {
      nomeDoMichael: "Michael Scott",
      clienteMichael: {
        nome: "Michael",
        email: "michael@gmail.com",
        idade: "9",
      },
    };
  },
  components: {
    Cliente,
    // Produto,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
