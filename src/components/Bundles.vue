<script setup>
import { ref } from 'vue'

const bundles = ref([
  {
    title: 'Daily Pass',
    price: '500 Ksh',
    icon: 'mdi-clock-outline',
    duration: '1 Day',
    features: ['Gym access', 'Locker use']
  },
  {
    title: 'Monthly Pass',
    price: '5,500 Ksh',
    icon: 'mdi-calendar-month',
    duration: '30 Days',
    features: ['Unlimited access', 'Locker', 'Free towel']
  },
  {
    title: '3 Months',
    price: '15,000 Ksh',
    icon: 'mdi-numeric-3-circle',
    duration: '90 Days',
    features: ['Everything + Free class', 'Trainer intro']
  },
  {
    title: '6 Months',
    price: '25,000 Ksh',
    icon: 'mdi-numeric-6-circle',
    duration: '180 Days',
    features: ['Premium access', '2 Free classes/mo']
  },
  {
    title: 'Annual Pass',
    price: '45,000 Ksh',
    icon: 'mdi-calendar-star',
    duration: '365 Days',
    features: ['VIP access', 'Unlimited classes', 'Personal plan']
  }
])
</script>

<template>
  <v-container class="py-12">
    <v-row>
      <v-col cols="12" class="text-center mb-16">
        <div class="text-h3 mb-4">Choose Your Perfect Bundle</div>
        <div class="text-subtitle-1 text-medium-emphasis mb-12">
          Select the plan that fits your fitness goals and schedule
        </div>
      </v-col>
    </v-row>

    <v-row>
      <v-col 
        v-for="(bundle, i) in bundles" 
        :key="i" 
        cols="12" 
        sm="6" 
        md="4" 
        lg="2.4"
      >
        <v-card 
          class="bundle-card pa-8 text-center elevation-8 fill-height hover"
          height="100%"
        >
          <div class="bundle-icon mb-6">
            <v-icon 
              :color="i === 0 ? 'warning' : 'primary'" 
              :icon="bundle.icon" 
              size="64"
            ></v-icon>
          </div>
          <div class="text-h5 font-weight-bold mb-2">{{ bundle.title }}</div>
          <div class="text-h4 font-weight-black primary--text mb-4">
            {{ bundle.price }}
          </div>
          <div class="text-body-1 text-medium-emphasis mb-6">
            {{ bundle.duration }}
          </div>
          <v-list density="compact" class="transparent pa-0 mb-6">
            <v-list-item v-for="(feature, j) in bundle.features" :key="j">
              <v-icon start small color="success">mdi-check-circle</v-icon>
              <v-list-item-title>{{ feature }}</v-list-item-title>
            </v-list-item>
          </v-list>
          <v-btn 
            color="primary" 
            variant="elevated" 
            block 
            rounded="xl"
            size="large"
            class="text-body-1 font-weight-bold"
          >
            Select Bundle
          </v-btn>
        </v-card>
      </v-col>
    </v-row>

    <v-row class="mt-16">
      <v-col cols="12" class="text-center">
        <v-card class="pa-12 mx-auto" max-width="800" color="surface" elevation="8" rounded="xl">
          <div class="text-h4 mb-4">Ready to start your fitness journey?</div>
          <div class="text-body-1 text-medium-emphasis mb-8">
            All bundles include 24/7 access, world-class equipment, 
            certified trainers, and a supportive community.
          </div>
          <v-btn 
            color="secondary" 
            size="x-large" 
            variant="elevated"
            class="px-12"
          >
            Get Started Today
          </v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.bundle-card {
  transition: all 0.3s ease;
  cursor: pointer;
}
.bundle-card.hover:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(29, 49, 36, 0.2) !important;
}
.bundle-icon {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(186, 206, 193, 0.2), rgba(246, 244, 232, 0.2));
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
}
</style>

