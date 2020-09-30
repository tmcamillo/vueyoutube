<template>
  <div id="cliente">
    <h4>Nome: {{ cliente.nome }}</h4>
    <h3>Email: {{ cliente.email }}</h3>
    <h3>Idade: {{ cliente.idade }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    nome: String,
    email: String,
    idade: Number,
    cliente: Object,
  },
};
</script>

<style scoped>
#cliente {
  color: rgb(6, 47, 80);
  background-color: rgb(244, 252, 255);
  padding: 4px;
  max-width: 50%;
  margin: 20px auto;
}
</style>
