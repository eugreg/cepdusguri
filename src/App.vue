<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      resultado: {},
    };
  },
  methods: {
    async search() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.resultado = data;
    },
  },
};
</script>
<template>
  <main>
    <h1>Busca Cep</h1>
    <form @submit.prevent="search">
      <input type="text" v-model="cep" />
      <button type="submit">buscar</button>
    </form>
    <form class="end">
      <label for="rua">rua</label>
      <input type="text" v-model="resultado.logradouro" />
      <label for="rua">bairro</label>
      <input type="text" v-model="resultado.bairro" />
      <label for="rua">cidade</label>
      <input type="text" v-model="resultado.localidade" />
      <label for="rua">estado</label>
      <input type="text" v-model="resultado.uf" />
      <label for="rua">ddd</label>
      <input type="text" v-model="resultado.ddd" />
    
    </form>
  </main>
</template>
<style>
  .end{
    display: flex;
    flex-direction: column;
  }
</style>
