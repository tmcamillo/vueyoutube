<template>
  <div id="cliente" v-if="cliente">
    <h4>Nome: {{ cliente.nome }}</h4>
    <h3>Email: {{ cliente.email }}</h3>
    <h3 v-if="showAge">Idade: {{ cliente.idade }}</h3>
    <h3 v-else>O usuário escondeu a idade!</h3>
    <h3 v-show="showAge">saiba mais</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    cliente: Object,
    showAge: Boolean,
  },
};
</script>

<style scoped>
#cliente {
  color: rgb(6, 47, 80);
  background-color: rgb(192, 236, 252);
  padding: 4px;
  max-width: 50%;
  margin: 20px auto;
}
</style>
