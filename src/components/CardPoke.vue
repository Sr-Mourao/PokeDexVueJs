<template>
  <v-card class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="450px"
      :src="url" 
    >
    </v-img>

    <v-card-title class="pb-0"> {{name}} </v-card-title>

    <v-card-text class="text--primary">
      <div>Habilidades</div>

      <div>peso</div>

      <div>altura</div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="orange" text> Share </v-btn>

      <v-btn color="orange" text> Explore </v-btn>
    </v-card-actions>
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
    };
  },

  beforeMount() {
    api
      .get("/pokemon/2/")
      .then( (response) => {
        console.log(response);
        this.name = response.data.name;
        this.url = response.data.sprites.other.dream_world.front_default;
      })
      .catch((error) => {
        console.log(error);
      })
      .then(() => {
      });
  },
};

</script>
