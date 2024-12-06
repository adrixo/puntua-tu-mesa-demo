<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-card class="mx-auto" max-width="400" elevation="2">
      <v-img
      height="200px"
      src="/cooker.jpeg"
      cover
    ></v-img>


      <v-card-title class="text-h6">
        La Cocina de Alan
      </v-card-title>
      <v-card-subtitle>
        The lovely City center house
      </v-card-subtitle>
      <v-card-text>
        This restaurant offers a variety of delicious dishes with excellent service. Come and enjoy a unique culinary experience. Burgers are recomended
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
          @click="handleRatingChange"
        />
      </v-card-actions>

      <v-expand-transition>
        <div v-if="showFeedback" class="pa-3">
          <v-typography variant="subtitle1" class="mb-3">
            We're sorry to hear your experience wasn't great. Please let us know how we can improve:
          </v-typography>
          <v-textarea
            v-model="feedback"
            label="Your Feedback"
            variant="outlined"
            density="comfortable"
            auto-grow
            rows="2"
            placeholder="Write your feedback here..."
          />
          <v-btn color="primary" class="mt-4" @click="submitFeedback">
            Submit Feedback
          </v-btn>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'RateCard',  
  data() {
    return {
      rating: 0, // Track the user's selected rating
      maps: "https://maps.app.goo.gl/Y5zMaVWpu5QaL9Vw7",
      showFeedback: false,
      feedback: ""
    };
  },
  methods: {
    handleRatingChange(value) {
      console.log("clicked")
      if (this.rating >= 4) {
        window.open(this.maps); 
      } else {
        this.showFeedback = true
      }
    },
    submitFeedback() {

    }
  },
};

</script>

<style scoped>
/* Add any custom styling here if needed */
</style>
