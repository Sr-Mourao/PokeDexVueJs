<template>
  <v-footer class="footer"  padless>
    <v-card class="flex" tile>
      <v-card-text class="py-2 white--text primary text-center">
        {{ new Date().getFullYear() }} — <strong>Felipe Mourão</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
};
</script>

<style scoped>
  .footer{
    padding-top: 30px;
  }
</style>