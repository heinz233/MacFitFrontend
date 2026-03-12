<script setup>
import { ref, onMounted } from 'vue'

const userDetails = ref({})
const isLoggedIn = ref(false)

onMounted(() => {
  const details = JSON.parse(localStorage.getItem('userDetails') || '{}')
  userDetails.value = details
  isLoggedIn.value = localStorage.getItem('isLoggedIn') === 'true'
})
</script>

<template>
  <v-container class="py-12">
    <v-row v-if="!isLoggedIn">
      <v-col cols="12" class="text-center">
        <div class="text-h5 mb-4">Please log in to view your profile</div>
        <v-btn color="primary" to="/login" size="large">Go to Login</v-btn>
      </v-col>
    </v-row>

    <v-row v-else>
      <v-col cols="12" md="8">
        <v-card class="elevation-8">
          <v-card-title class="text-h4">
            <v-icon start size="48" color="primary">mdi-account-circle</v-icon>
            My Profile
          </v-card-title>
          <v-card-text>
            <v-row>
              <v-col cols="12" md="6">
                <v-list density="compact">
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Full Name</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.name }}</v-list-item-subtitle>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Email</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.email }}</v-list-item-subtitle>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Phone</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.phone }}</v-list-item-subtitle>
                  </v-list-item>
                </v-list>
              </v-col>
              <v-col cols="12" md="6">
                <v-list density="compact">
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Date of Birth</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.dob }}</v-list-item-subtitle>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Gender</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.gender }}</v-list-item-subtitle>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-title class="font-weight-bold">Gym Location</v-list-item-title>
                    <v-list-item-subtitle>{{ userDetails.gymLocation }}</v-list-item-subtitle>
                  </v-list-item>
                </v-list>
              </v-col>
            </v-row>
          </v-card-text>
          <v-card-actions class="pa-6">
            <v-spacer></v-spacer>
            <v-btn color="primary" size="large">Edit Profile</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" md="4">
        <v-card class="elevation-4 pa-6 text-center">
          <v-avatar size="120" class="mb-4">
            <v-icon size="80">mdi-account-circle</v-icon>
          </v-avatar>
          <div class="text-h6 font-weight-bold mb-2">{{ userDetails.name }}</div>
          <v-chip color="secondary" class="mb-4">Member</v-chip>
          <v-progress-circular 
            :rotate="-90"
            :size="120"
            :width="12"
            color="primary"
            :model-value="85"
          >
            85%
          </v-progress-circular>
          <div class="text-body-1 mt-2">Fitness Goal Progress</div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

