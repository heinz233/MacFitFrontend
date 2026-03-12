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
  <v-container style="background-color:#E3F2FD" max-width="50%" mt="12">
    <v-row>
        <v-col>
            <v-card>
                <v-img src="" class="h-50" cover></v-img>
                <v-card-title>{{ userDetails.name }}</v-card-title>
                <v-card-text>{{ userDetails.email }}</v-card-text>
                <v-card-text>{{ userDetails.phone }}</v-card-text>
                <v-card-text>{{ userDetails.gymLocation }}</v-card-text>
                  <div v-if="userDetails.subscription">
                    <v-card-text>Your current subscription is{{ userDetails.subscription.name }} at {{ userDetails.subription.price }}</v-card-text>
                  </div>
                  <div v-else>
                    <v-btn color="primary" variant="outlined" to="/bundles">Select a Bundle</v-btn>
                  </div>            
            </v-card>
        </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
/* Gym-themed profile styles */
v-container {
  background: linear-gradient(135deg, #0f2027 0%, #203a43 50%, #2c5364 100%) !important;
  min-height: 100vh;
  padding: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

v-card {
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.9);
  border-radius: 24px;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.2);
  overflow: hidden;
  max-width: 400px;
  width: 100%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

v-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 35px 60px rgba(0, 0, 0, 0.3);
}

:deep(.v-img) {
  position: relative;
  height: 200px;
  background: linear-gradient(45deg, #667eea 0%, #764ba2 100%);
}

:deep(.v-img)::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background-image: url('/macfit.png');
  background-size: cover;
  background-position: center;
  border: 5px solid white;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  z-index: 2;
}

:deep(.v-img)::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 50%;
  background: linear-gradient(transparent, rgba(0,0,0,0.5));
  z-index: 1;
}

:deep(.v-card-title) {
  font-size: 2.5rem;
  font-weight: bold;
  color: #1a365d;
  text-align: center;
  margin: 1rem 0;
  text-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

:deep(.v-card-text) {
  font-size: 1.1rem;
  color: #4a5568;
  margin-bottom: 0.5rem;
  text-align: center;
}

:deep(.v-btn) {
  background: linear-gradient(45deg, #ff6b6b, #feca57);
  color: white !important;
  border-radius: 50px !important;
  font-weight: bold;
  text-transform: none;
  padding: 0 2rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(254, 202, 87, 0.4);
}

:deep(.v-btn:hover) {
  transform: scale(1.05);
  box-shadow: 0 8px 25px rgba(254, 202, 87, 0.6);
}

/* Responsive */
@media (max-width: 768px) {
  v-container {
    padding: 1rem;
  }
  
  v-card {
    max-width: 90%;
  }
  
  :deep(.v-card-title) {
    font-size: 2rem;
  }
}
</style>

