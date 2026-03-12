<script setup>
import { ref } from 'vue'

const userStats = ref({
  workouts: 12,
  calories: 2450,
  streak: 5
})
</script>

<template>
  <v-container max-width="100%" class="py-8">
    <!-- Hero Section -->
    <v-row class="text-center mb-12">
      <v-col md="12">
        <div class="text-display-medium mb-4">Welcome Back to MacFit!</div>
        <div class="text-title-large font-weight-light text-medium-emphasis mb-8">
          Continue your fitness journey. Today's goal: Stay strong, stay consistent.
        </div>
        <v-img 
          src="/carousel1.jpg" 
          class="rounded-xl mx-auto mb-4" 
          max-width="800" 
          height="400"
          cover
        ></v-img>
      </v-col>
    </v-row>

    <!-- Quick Stats -->
    <v-row class="mb-12">
      <v-col md="4">
        <v-card class="text-center pa-6 elevation-4">
          <div class="text-h4 font-weight-bold text-primary">{{ userStats.workouts }}</div>
          <div class="text-title-medium text-medium-emphasis">Workouts this month</div>
        </v-card>
      </v-col>
      <v-col md="4">
        <v-card class="text-center pa-6 elevation-4">
          <div class="text-h4 font-weight-bold text-primary">{{ userStats.calories }}</div>
          <div class="text-title-medium text-medium-emphasis">Calories burned</div>
        </v-card>
      </v-col>
      <v-col md="4">
        <v-card class="text-center pa-6 elevation-4">
          <div class="text-h4 font-weight-bold text-primary">{{ userStats.streak }} days</div>
          <div class="text-title-medium text-medium-emphasis">Streak</div>
        </v-card>
      </v-col>
    </v-row>

    <!-- Quick Links -->
    <v-row class="mb-12">
      <v-col md="12">
        <div class="text-title-large font-weight-medium mb-8 text-center">Quick Actions</div>
      </v-col>
      <v-col md="3">
        <v-btn 
          to="/profile" 
          color="#3A4B68" 
          variant="elevated" 
          block 
          size="large"
          class="mb-4"
        >
          View Profile
        </v-btn>
      </v-col>
      <v-col md="3">
        <v-btn 
          to="/bundles" 
          color="#3A4B68" 
          variant="elevated" 
          block 
          size="large"
          class="mb-4"
        >
          Browse Bundles
        </v-btn>
      </v-col>
      <v-col md="3">
        <v-btn 
          to="/gymlocations" 
          color="primary" 
          variant="elevated" 
          block 
          size="large"
          class="mb-4"
        >
          Find Gym
        </v-btn>
      </v-col>
      <v-col md="3">
        <v-btn 
          color="#3A4B68" 
          variant="elevated" 
          block 
          size="large"
          class="mb-4"
        >
          Start Workout
        </v-btn>
      </v-col>
    </v-row>

    <!-- Featured Bundles Teaser -->
    <v-row class="mb-12">
      <v-col md="12">
        <div class="text-title-large font-weight-medium mb-8 text-center">Featured Bundles</div>
      </v-col>
      <v-col md="4">
        <v-card class="pa-4 elevation-2">
          <v-img src="/abdullah-ali-L2Nw-onZOX4-unsplash.jpg" height="200" cover></v-img>
          <v-card-title>Beginner Bundle</v-card-title>
          <v-card-text>Perfect for starters - 3 months access</v-card-text>
          <v-btn color="#3A4B68" block>View Details</v-btn>
        </v-card>
      </v-col>
      <v-col md="4">
        <v-card class="pa-4 elevation-2">
          <v-img src="/ambitious-studio-rick-barrett-1RNQ11ZODJM-unsplash.jpg" height="200" cover></v-img>
          <v-card-title>Pro Bundle</v-card-title>
          <v-card-text>Unlimited access + PT sessions</v-card-text>
          <v-btn color="#3A4B68" block>View Details</v-btn>
        </v-card>
      </v-col>
      <v-col md="4">
        <v-btn 
          to="/bundles" 
          size="large" 
          color="#3A4B68" 
          variant="elevated"
          block
        >
          See All Bundles
        </v-btn>
      </v-col>
    </v-row>

    <!-- CTA Section -->
    <v-row class="text-center mb-12" style="background-color: #CFD0D6; padding: 4rem 0;">
      <v-col md="12">
        <div class="text-title-large font-weight-medium mb-4">Ready to crush your goals?</div>
        <v-btn 
          to="/gymlocations" 
          color="primary" 
          size="large" 
          variant="elevated"
        >
          Find Nearest Gym
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

