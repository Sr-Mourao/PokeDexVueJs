<template>
  <v-card elevation="5" class="mx-auto card" max-width="450">
    <v-toolbar flat color="transparent">
      <v-text-field
        v-model="search"
        label="Digite o personagem"
        single-line
      ></v-text-field>
      <v-btn @click="getPokemon">Pesquisar</v-btn>
    </v-toolbar>
    <v-img class="white--text align-end" width="500px" :src="url"> </v-img>

    <v-card-title class="pb-0"> Nome: {{ name }} </v-card-title>

    <v-card-text class="text--primary">
      <h3>ID: {{ id }}</h3>

      <tr v-for="habilidade in habilidades" :key="habilidade.id">
        <td>Habilidades: {{ habilidade.ability.name }}</td>
      </tr>

      <div>Peso: {{ peso }}</div>

      <div>Altura: {{ altura }}</div>
    </v-card-text>
  </v-card>
</template>



<script>
import api from "../services/api";
import Swal from "sweetalert2/dist/sweetalert2.js";


const Toast = Swal.mixin({
  toast: true,
  position: "top-end",
  timer: 3000,
  timerProgressBar: true,
  showConfirmButton: false,
});

export default {
  name: "App",

  data() {
    return {
      name: "",
      url: "",
      id: "",
      habilidades: [],
      peso: "",
      altura: "",
      search: "charizard",
    };
  },

  async beforeMount() {
    await this.getPokemon();
  },

  methods: {
    getPokemon() {
      api
        .get(`/pokemon/${this.search}/`)
        .then((response) => {
          this.name = response.data.name;
          this.id = response.data.id;
          this.habilidades = response.data.abilities;
          this.peso = response.data.weight;
          this.altura = response.data.height;
          this.url = response.data.sprites.other.dream_world.front_default;
          this.toastPositivo();
        })
        .catch((error) => {
          this.toastNegative();
          return error;
        });
    },
    toastPositivo() {
      Toast.fire("Pokemon encontrado!", "", "success");
    },
    toastNegative() {
      Toast.fire("Ocorreu um erro, tente novamente!", "", "error");
    },
  },
};
</script>

<style scoped>
.card {
  margin-top: 10px;
}
</style>