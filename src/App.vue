<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>PokeDex</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>

  <v-main> 
    <CardPoke />
    <FooterVue />
  </v-main>
  </v-app>
</template>

<script>
import CardPoke from "./components/CardPoke"
import FooterVue from "./components/FooterVue.vue"
export default {
  name: "App",
  components: {
    CardPoke,
    FooterVue
}
};
</script>

