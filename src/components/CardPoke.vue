<template>
  <v-card class="mx-auto card" max-width="400">
     <v-toolbar
      flat
      color="transparent"
    > 
      <v-text-field
        v-model="search"
        label="Digite o personagem"
        single-line 
      ></v-text-field>
      <v-btn @click="getPokemon">Pesquisar</v-btn>
    </v-toolbar>
    <v-img class="white--text align-end" height="450px" :src="url"> </v-img>

    <v-card-title class="pb-0"> Nome: {{ name }} </v-card-title>

    <v-card-text class="text--primary">
      <div>Habilidades:</div>

      <div>Peso: {{peso}}</div>

      <div>Altura: {{altura}}</div>
    </v-card-text>
  </v-card>
</template>



<script>
import api from "../services/api";

export default {
  name: "App",

  data() {
    return {
      name: "",
      url: "",
      habilidades: "",
      peso: "",
      altura: "",
      search: "charizard"

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
        this.habilidades = response.data.abilities;
        this.peso = response.data.weight;
        this.altura = response.data.height;
        this.url = response.data.sprites.other.dream_world.front_default;
      })
      .catch((error) => {
        return error;
      })
      .then(() => {});
    },
    }
  
};
</script>

<style scoped>
.card {
  margin-top: 30px;
}
</style>