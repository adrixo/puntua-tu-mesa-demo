<template>
    <v-app-bar app dense>
      <v-spacer></v-spacer>
      <v-img
            height="100%"
            src="/logo-transparent.webp"
            class="logo"
            cover
        ></v-img>
      <v-spacer></v-spacer>
    </v-app-bar>
  </template>
  
  <script>
  </script>
  
  <style scoped>
    .logo {
    height: 38px; /* Adjust height to fit your topbar */
    max-width: 100px; /* Ensure it doesn't stretch too much */
    object-fit: contain; /* Ensure aspect ratio is preserved */
  }

  </style>
  