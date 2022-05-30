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
      <v-btn>Pesquisar</v-btn>
    </v-toolbar>
    <v-img class="white--text align-end" height="450px" :src="url"> </v-img>

    <v-card-title class="pb-0"> {{ name }} </v-card-title>

    <v-card-text class="text--primary">
      <div>Habilidades</div>

      <div>peso</div>

      <div>altura</div>
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
      search: ""

    };
  },

  beforeMount() {},

  methods: {
    getPokemon() {
       api
      .get('/pokemon/2/')
      .then((response) => {
        console.log(response);
        this.name = response.data.name;
        this.url = response.data.sprites.other.dream_world.front_default;
      })
      .catch((error) => {
        console.log(error);
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