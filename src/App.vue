<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>PokeDex</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>

  <v-main> 
    <CardTop />
    <CardPoke />
    <FooterVue />
    
  </v-main>
  </v-app>
</template>

<script>
import CardTop from "./components/CardTop.vue"
import CardPoke from "./components/CardPoke"
import FooterVue from "./components/FooterVue.vue"

export default {
  name: "App",
  components: {
    CardTop,
    CardPoke,
    FooterVue
}
};
</script>

