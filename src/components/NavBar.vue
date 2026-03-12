<script setup>
</script>

<template>
  <v-app-bar color="secondary" elevation="4" height="70">
    <v-app-bar-title>MacFit Gym</v-app-bar-title>
    <v-spacer></v-spacer>
    <v-btn 
      variant="text" 
      to="/" 
      class="mr-2"
    >
      Landing
    </v-btn>
    <v-btn 
      variant="text" 
      to="/homepage" 
      class="mr-2"
    >
      Home
    </v-btn>
    <v-btn 
      variant="text" 
      to="/bundles" 
      class="mr-2"
    >
      Bundles
    </v-btn>
    <v-btn 
      variant="text" 
      to="/gymlocations" 
      class="mr-2"
    >
      Locations
    </v-btn>
    <v-btn 
      variant="text" 
      to="/profile" 
      class="mr-2"
    >
      Profile
    </v-btn>
    <v-btn 
      variant="text" 
      to="/login" 
      class="mr-2"
    >
      Login
    </v-btn>
    <v-btn 
      variant="text" 
      to="/signup"
    >
      Sign Up
    </v-btn>
  </v-app-bar>
</template>
