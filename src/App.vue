<template>
  <div id="app">
    <h1>Guia Clientes</h1>
    <Cliente :cliente="clienteMichael" :showAge="true" />
    <Cliente :cliente="clienteMichael" :showAge="false" />

    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <p>{{ index + 1 }}</p>
      <input type="text" v-model="clienteMichael.nome" />
      <input type="text" v-model="clienteMichael.email" />
      <Cliente :cliente="cliente" />
    </div>
  </div>
</template>

<script>
import Cliente from "./components/Cliente";

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
      clientes: [
        {
          id: 1,
          nome: "Pam",
          email: "pam@gmail.com",
          idade: "45",
        },
        {
          d: 3,
          nome: "Dwight",
          email: "dwight@gmail.com",
          idade: "10",
        },
        {
          d: 67,
          nome: "Jim",
          email: "jim@gmail.com",
          idade: "45",
        },
        {
          d: 5,
          nome: "Petra",
          email: "petra@gmail.com",
          idade: "33",
        },
        {
          d: 55,
          nome: "Valery",
          email: "valery@gmail.com",
          idade: "2",
        },
      ],
    };
  },
  components: {
    Cliente,
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
