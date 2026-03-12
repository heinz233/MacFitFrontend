<script setup>
</script>

<template>
  <v-container fluid class="fill-height pa-0">
    <!-- Hero Carousel -->
    <v-row class="fill-height">
      <v-col cols="12">
        <v-carousel 
          cycle 
          height="100vh" 
          hide-delimiter-background 
          show-arrows
          class="hero-carousel"
        >
          <v-carousel-item v-for="n in 4" :key="n">
            <v-img 
              :src="`/abdullah-ali-L2Nw-onZOX4-unsplash.jpg`" 
              cover
              gradient="to right, rgba(29,49,36,0.6), rgba(29,49,36,0.4)"
            >
              <v-row class="fill-height pa-16" align="center">
                <v-col cols="12" md="7">
                  <div class="hero-content">
                    <div class="text-h2 font-weight-black mb-4 text-white drop-shadow">
                      Welcome to MacFit Gym
                    </div>
                    <div class="text-h5 font-weight-medium mb-12 text-white drop-shadow">
                      World-class fitness in Nairobi. Transform your body, elevate your life.
                    </div>
                    <v-btn 
                      color="primary" 
                      size="x-large" 
                      variant="elevated"
                      class="px-12 mb-4 me-4"
                    >
                      Join Now
                    </v-btn>
                    <v-btn 
                      color="white" 
                      variant="tonal" 
                      size="large"
                      class="px-8"
                    >
                      Learn More
                    </v-btn>
                  </div>
                </v-col>
              </v-row>
            </v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>

    <!-- Features Section -->
    <v-container class="py-16">
      <v-row class="text-center mb-16">
        <v-col cols="12">
          <div class="text-h4 font-weight-bold mb-4">Why Choose MacFit?</div>
        </v-col>
      </v-row>
      <v-row>
        <v-col v-for="n in 6" :key="n" cols="12" sm="6" md="4" lg="2">
          <v-card 
            class="pa-8 text-center hover-lift" 
            color="surface" 
            rounded="lg"
            elevation="4"
          >
            <v-icon 
              :color="n%2 ? 'secondary' : 'primary'" 
              :size="48" 
              class="mb-6"
            >
              mdi-weight-lifter
            </v-icon>
            <div class="text-h6 font-weight-bold mb-4">Feature {{ n }}</div>
            <div class="text-body-1 text-medium-emphasis">
              World-class equipment and training programs for all levels.
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <!-- Stats Section -->
<v-container color="primary" class="py-16 text-white">
      <v-row class="text-center">
        <v-col cols="12" md="3">
          <div class="text-h3 font-weight-black mb-1">50K+</div>
          <div class="text-h6">Happy Members</div>
        </v-col>
        <v-col cols="12" md="3">
          <div class="text-h3 font-weight-black mb-1">10+</div>
          <div class="text-h6">Locations</div>
        </v-col>
        <v-col cols="12" md="3">
          <div class="text-h3 font-weight-black mb-1">24/7</div>
          <div class="text-h6">Access</div>
        </v-col>
        <v-col cols="12" md="3">
          <div class="text-h3 font-weight-black mb-1">5⭐</div>
          <div class="text-h6">Rating</div>
        </v-col>
      </v-row>
    </v-container>

    <!-- CTA Section -->
    <v-container class="py-16 text-center">
      <v-sheet 
        color="surface" 
        rounded="xl" 
        elevation="12"
        class="pa-16 mx-auto"
        max-width="800"
      >
        <div class="text-h3 font-weight-bold mb-4">Ready to Transform?</div>
        <div class="text-body-1 text-medium-emphasis mb-12">
          Join thousands of members achieving their fitness goals at MacFit Gym.
        </div>
        <v-row justify="center">
          <v-col cols="auto">
            <v-btn 
              color="primary" 
              size="x-large" 
              variant="elevated"
              class="px-16 me-4"
            >
              Get Started
            </v-btn>
            <v-btn 
              color="secondary" 
              size="large" 
              variant="outlined"
              class="px-8"
            >
              View Locations
            </v-btn>
          </v-col>
        </v-row>
      </v-sheet>
    </v-container>
  </v-container>
</template>

<style scoped>
.hero-carousel :deep(.v-carousel__controls) {
  display: none;
}
.drop-shadow {
  text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
}
.hover-lift {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.hover-lift:hover {
  transform: translateY(-8px);
}
</style>

