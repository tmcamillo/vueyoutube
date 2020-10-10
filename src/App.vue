<template>
  <div id="app">

    <h1>Cadastro</h1>
    <small class="name-error" v-show="deuErro">O nome é inválido, tente novamente</small>
    <input type="text" placeholder="nome" v-model="nameField" />
    <input type="email" placeholder="email" v-model="emailField" />
    <input type="number" placeholder="idade" v-model="ageField" />
    <button @click="cadastrarUsuario">Cadastrar</button>

    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <p>{{ index + 1 }}</p>
      <Cliente :cliente="cliente" @meDelete="deletarUsuario($event)"/>
    </div>

  </div>
</template>

<script>
import Cliente from "./components/Cliente";

export default {
  name: "App",
  data() {
    return {
      deuErro: false,
      nameField: "",
      emailField: "",
      ageField: "",
      clientes: [
        {
          id: 1,
          nome: "Pam",
          email: "pam@gmail.com",
          idade: "45",
        },
        {
          id: 3,
          nome: "Dwight",
          email: "dwight@gmail.com",
          idade: "10",
        },
        {
          id: 67,
          nome: "Jim",
          email: "jim@gmail.com",
          idade: "45",
        },
        {
          id: 5,
          nome: "Petra",
          email: "petra@gmail.com",
          idade: "33",
        },
        {
          id: 55,
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
  methods: {
    cadastrarUsuario() {
      if (this.nameField == "" ||this.nameField == "" ||this.nameField.length == "") {
        this.deuErro = true;
      } 
      else {
        this.clientes.push({nome: this.nameField, email: this.emailField, idade: this.ageField, id: Date.now()});
        (this.nameField = ""), (this.emailField = ""), (this.ageField = "");
        this.deuErro = false;
      }
    },
    deletarUsuario($event) { //passando dados do filho para o pai com eventos
      let id = $event.idCliente;
      let novoArray = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = novoArray;
    }
  },
  computed:{
    orderClientes(){
      let clientes = Object.assign([],this.clientes) //mantem lista original
      console.log(clientes.sort((a, b)=> (a.nome.toUpperCase() > b.nome.toUpperCase() ? 1 : -1)))
      return clientes.sort((a, b)=> (a.nome.toUpperCase() > b.nome.toUpperCase()) ? 1 : -1)
    }
  }
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
.name-error {
  color: red;
}
</style>
