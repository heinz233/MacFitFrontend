<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const rules = {
  required: value => !!value || 'Required.',
  min: v => v.length >= 8 || 'Min 8 characters',
  emailMatch: () => (`The email and password you entered don't match`),
}

const show1 = ref(false)
const username = ref('')
const password = ref('')

const errorMessage = ref('')

const isFormValid = computed(() => username.value && password.value)

function login(){
  const userDetails = JSON.parse(localStorage.getItem('userDetails') || '{}')
  
  if (username.value === userDetails.email && password.value === userDetails.password) {
    localStorage.setItem('isLoggedIn', 'true')
    router.push('/homepage')
  } else {
    errorMessage.value = 'Invalid credentials. Please try again.'
    setTimeout(() => { errorMessage.value = '' }, 5000)
  }
}
</script>

<template>
  <v-container color="surface" width="50%" class="text-center mt-12">
    <v-row>
      <v-col md="12">
        <div class="text-h4 font-weight-bold mb-8">Welcome Back</div>
        <v-form @submit.prevent="login">
          <v-row>
            <v-col md="6">
              <div class="text-title-large font-weight-medium text-right">Email</div>
            </v-col>
            <v-col md="6">
              <v-text-field 
                v-model="username"
                :rules="[rules.required]"
                variant="outlined"
                label="Email"
              ></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col md="6">
              <div class="text-title-large font-weight-medium text-right">Password</div>
            </v-col>
            <v-col md="6">
              <v-text-field 
                v-model="password"
                :rules="[rules.required, rules.min]"
                :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                :type="show1 ? 'text' : 'password'"
                variant="outlined"
                label="Password"
                @click:append="show1 = !show1"
              ></v-text-field>
            </v-col>
          </v-row>
          <v-row v-if="errorMessage" justify="center">
            <v-col md="12">
              <v-alert type="error" density="comfortable" class="mb-4">
                {{ errorMessage }}
              </v-alert>
            </v-col>
          </v-row>
          <v-row>
            <v-col md="12">
              <v-btn 
                color="primary" 
                variant="elevated" 
                size="large"
                block
                :disabled="!isFormValid"
                type="submit"
              >
                Login
              </v-btn>
            </v-col>
          </v-row>
          <v-row>
            <v-col md="12">
              <div class="mt-4">
                New to MacFit? <router-link to="/signup" class="text-primary font-weight-medium">Create an account</router-link>
              </div>
            </v-col>
          </v-row>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>
