<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-card class="mx-auto" max-width="400" elevation="2">
      <v-img
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      cover
    ></v-img>


      <v-card-title class="text-h6">
        Restaurant Name
      </v-card-title>
      <v-card-subtitle>
        A great place to dine
      </v-card-subtitle>
      <v-card-text>
        This restaurant offers a variety of delicious dishes with excellent service. Come and enjoy a unique culinary experience.
      </v-card-text>
      <v-card-actions class="d-flex justify-center">
        <!-- Rating Component -->
        <v-rating
          v-model="rating"
          length="5"
          size="32"
          color="yellow"
          background-color="grey lighten-2"
          hover
          dense
        />
      </v-card-actions>

    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'RateCard',
};
</script>

<style scoped>
/* Add any custom styling here if needed */
</style>
