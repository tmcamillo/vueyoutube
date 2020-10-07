/* eslint no-use-before-define: 0 */
<template>
  <div
    :class="{ cliente: !isPremium, 'cliente-premium': isPremium }"
    v-if="cliente"
  >
    <h4>Nome: {{ cliente.nome | processarEmail }}</h4>
    <h3>Email: {{ cliente.email }}</h3>
    <h3 v-if="showAge">Idade: {{ cliente.idade }}</h3>
    <h3 v-else>O usuário escondeu a idade!</h3>
    <h3 v-show="showAge">saiba mais</h3>
    <button @click="mudarCor($event)">Mudar cor</button>
    <button @click="emitirEventoDelete()">Deletar</button>

  </div>
</template>

<script>
export default {
  data() {
    return {
      isPremium: true,
    };
  },
  props: {
    cliente: Object,
    showAge: Boolean,
  },
  methods: {
    mudarCor($event) {
      console.log($event);
      this.isPremium = !this.isPremium;
    },
    emitirEventoDelete(){
      console.log('emitindo do filho');
      this.$emit("meDelete", {idCliente: this.cliente.id, curso: 'Formacao Vue', emPromocao: true, component: this} );
    },
    testar(){
      console.log("testando para valer!")
      alert("Isso é um alert")
    }
  },
  filters: {
    processarEmail(value){
      return value.toUpperCase();
    }
  }
};
</script>

<style scoped>
  .cliente {
    color: rgb(6, 47, 80);
    background-color: rgb(117, 186, 243);
    padding: 4px;
    max-width: 50%;
    margin: 20px auto;
  }

  .cliente-premium {
    color: rgb(117, 186, 243);
    background-color: rgb(6, 47, 80);
    padding: 4px;
    max-width: 50%;
    margin: 20px auto;
  }
</style>
