<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
    };
  },
  methods: {
    async search() {
      const url = `https://www.cepaberto.com/api/v3/cep?cep=${this.cep}`;
      this.resultado = await axios.get(url, {
        headers: {
          Authorization: "token token=0991bb7dd912811e5252a9b907d19311",
        },
      });
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
    {{ resultado }}
  </main>
</template>
