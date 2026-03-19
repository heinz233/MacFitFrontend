<script setup>
    const userDetails = JSON.parse(localStorage.getItem('user'))
    
</script>

<template>
    <v-container width="50%" style="background-color:#CFD0D6" class="mt-12 " align="center" justify="center">
        <v-row>
            <v-col>
                <v-card width="50%">
                    <v-img src="/profilepic.png" class="h-50" cover></v-img>
                    <v-card-title>{{ userDetails.name }}</v-card-title>
                    <v-card-text>{{ userDetails.email }}</v-card-text>
                    <v-card-text>{{ userDetails.phoneNumber }}</v-card-text>
                    <v-card-text>{{ userDetails.gym_location }}</v-card-text>
                    <div v-if="userDetails.subscription" class="mb-8">
                        <v-card-text>Your current subscription is: {{ userDetails.subscription.name }} at {{ userDetails.subscription.price }}</v-card-text>
                    </div>
                    <div v-else class="mb-8">
                        <v-btn color="primary" variant="elevated" to="/bundles"> Select a Bundle</v-btn>
                    </div>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>