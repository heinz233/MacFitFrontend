<script setup>
import {ref} from 'vue'
import {useRouter} from "vue-router";

const router = useRouter();

const showBundleDialog = ref(false)
const isLoggedIn = localStorage.getItem( "authToken")
const selectedBundle = ref(null)
const selectedPrice = ref(null)

function showBundle(name, price){
    if(isLoggedIn){
        selectedBundle.value = name
        selectedPrice.value = price
        showBundleDialog.value = true //open popup
    }else{
        router.push('/login')
    }
}
function subscribe(){
    const userDetails = JSON.parse(localStorage.getItem('user'))
    userDetails.subscription = {
        name: selectedBundle.value,
        price: selectedPrice.value
    }
    localStorage.setItem('user', JSON.stringify(userDetails))
    showBundleDialog.value = false

}


</script>

<template>
    <v-container style="background-color:#CFD0D6" class="mt-12">
        <v-row>
            <div class="text-display-medium mb-6">Bundles and Pricing</div>
        </v-row>
        <v-row>
            <div class="text-label-medium font-italic">Click on a bundle to subscribe </div>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card class="text-center" @click="showBundle('Daily Pass',500)">
                    <v-icon color="#3A4B68" icon="mdi-clock-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">Daily Pass</v-card-title>
                    <v-card-text>500 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" @click="showBundle('1 Month',5500)">
                    <v-icon color="#3A4B68" icon="mdi-calendar-blank" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">1 Month</v-card-title>
                    <v-card-text>5500 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" @click="showBundle('3 Months',15000)">
                    <v-icon color="#3A4B68" icon="mdi-numeric-3-circle-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">3 Months</v-card-title>
                    <v-card-text>15000 Ksh</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" @click="showBundle('6 Monthd',25000)">
                    <v-icon color="#3A4B68" icon="mdi-numeric-6-circle-outline" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">6 Months</v-card-title>
                    <v-card-text>25000 Ksh</v-card-text>
                </v-card>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="12">
                <v-card class="text-center" @click="showBundle('12 Months',45000)">
                    <v-icon color="#3A4B68" icon="mdi-timer-sand-full" size="large" class="mt-8"></v-icon>
                    <v-card-title color="#3A4B68">12 Months</v-card-title>
                    <v-card-text>45000 Ksh</v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
    <!-- What's Included -->
     <v-container style="background-color:#CFD0D6" class="mt-12">
        <v-row>
            <v-col md="12">
                <div class="text-display-medium mb-12">What's included in your bundle</div>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-food-variant" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">Personalized Meal Plan</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-door" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">24/7 Gym Access</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-weight-lifter" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">World class trainers</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-run" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">Running club</v-card-text>
                </v-card>
            </v-col>
        </v-row>
        <v-row>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-hiking" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">Hiking club</v-card-text>
                </v-card>
            </v-col>
            <v-col md="3">
                <v-card class="text-center" hover>
                    <v-icon color="#3A4B68" icon="mdi-bike" size="large" class="mt-8"></v-icon>
                    <v-card-text color="#3A4B68">Cycling club</v-card-text>
                </v-card>
            </v-col>
        </v-row>
     </v-container>
     <!-- How to join -->
     <v-container style="background-color:#CFD0D6" class="mt-12">
        <v-row>
            <v-col>
                <div class="text-display-medium mt-8">How to join</div>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-list>
                    <v-list-item>1. Select your preffered bundle</v-list-item>
                    <v-list-item>2. Fill in the online form</v-list-item>
                    <v-list-item>3. Make a payment</v-list-item>
                    <v-list-item>4. Visit the gym to activate your account</v-list-item>
                </v-list>
            </v-col>
        </v-row>
     </v-container>
    <!-- Dialog -->
      <v-dialog v-model="showBundleDialog" max-width="600" >

      <v-card prepend-icon="mdi-account" title="Subscribe to Bundle" >
        <v-card-text>
          You are about to subscribe to {{ selectedBundle }} at {{ selectedPrice }}. Click on the button below to complete payment
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
         <v-spacer></v-spacer>
          <v-btn text="Close" variant="plain" @click="showBundleDialog = false" ></v-btn>
          <v-btn color="primary" variant="tonal" @click="subscribe()" >Subscribe</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>