<template>
  <v-container class="d-flex justify-center align-center" style="height: 70vh;">
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

          <v-card-text>
            We're sorry to hear your experience wasn't great. Please let us know how we can improve:
          </v-card-text>
          <v-textarea
            v-model="feedback"
            label="Your Feedback"
            variant="outlined"
            density="comfortable"
            auto-grow
            rows="2"
            placeholder="Write your feedback here..."
          />
          <v-card-actions>
            <v-btn
              text="Submit Feedback"
              block
              border
              @click="submitFeedback"
            ></v-btn>
          </v-card-actions>
        </div>
      </v-expand-transition>
    </v-card>


    <div>
      <!-- Dialog -->
      <v-dialog v-model="showPopup" max-width="400">
        <v-card class="mx-auto" max-width="400" elevation="2">
        <v-img
              src="/logo-transparent.webp"
              class="logo"
              cover
          ></v-img>
          <v-card-title class="text-h6 text-center">
            Thank you!
          </v-card-title>
          <v-card-text>
            Your feedback has been sent directly to our manager! We value your opinion.
          </v-card-text>
          <v-card-actions class="justify-center">
            <v-btn color="primary" text @click="acceptSubmit">
              Close
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>

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
      feedback: "",
      showPopup: false
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
      this.showPopup = true
    },
    acceptSubmit() {
      this.showFeedback = false
      this.showPopup = false
    }
  },
};

</script>

<style scoped>
/* Add any custom styling here if needed */
</style>
