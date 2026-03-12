<script setup>
    import { ref } from 'vue'

const rules = {
  required: value => !!value || 'Required.',
  min: v => v.length >= 8 || 'Min 8 characters',
  emailMatch: () => (`The email and password you entered don't match`),
}

const show1 = ref(false)
const show2 = ref(true)
const password = ref('')
const confirmPassword = ref('')
const show1confirm = ref(false)

// Form fields
const firstName = ref('null')
const lastName = ref('null')
const username = ref('null')
const email = ref('null')
const dateOfBirth = ref('null')
const phone = ref('null')
const gender = ref('null')
const gymLocation = ref('null')

function signUp(){
        const userDetails  = {
            name: firstName.value + lastName.value,
            email: email.value,
            phone: phone.value,
            dob: dateOfBirth.value,
            gender: gender.value,
            gymLocation: gymLocation.value,
            password: password.value,
        }

        try{
            localStorage.setItem('userDetails', JSON.stringify(userDetails))
        }catch(err){
            console.error('Sign up process failed')
        }
}
</script>

<template>
    <v-container color="#CFD0D6" width="50%" class="text-center mt-12">
        <v-row>
            <v-col md="12">
                <v-form>
                    <v-row>
                        <v-col md="12">
                            <v-img src="/public/"></v-img>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col>
                            <div class="text-title-large font-weight-medium">Sign up to Macfit gym</div>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">First Name</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field v-model="firstName" variant="outlined"></v-text-field>
                        </v-col>
                    
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Second Name</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field v-model="lastName" variant="outlined"></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>                 
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Username</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field v-model="username" variant="outlined"></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>                 
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Email Address</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field v-model="email" variant="outlined"></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Date Of Birth</div>
                        </v-col>
                        <v-col md="6">
                          <v-text-field
                            label="Date input"
                            variant="outlined"
                            type="date"
                            v-model="dateOfBirth"
                          ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Password</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field 
                                variant="outlined"
                                v-model="password"
                                :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                                :rules="[rules.required, rules.min]"
                                :type="show1 ? 'text' : 'password'"
                                @click:append="show1 = !show1"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                     <v-row>
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Confirm Password</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field 
                                variant="outlined"
                                v-model="confirmPassword"
                                :append-icon="show1confirm ? 'mdi-eye' : 'mdi-eye-off'"
                                :rules="[rules.required, rules.min]"
                                :type="show1confirm ? 'text' : 'password'"
                                @click:append="show1confirm = !show1confirm"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>                 
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Gym Location</div>
                        </v-col>
                        <v-col md="6">
                            <v-select
                                v-model="gymLocation"
                                label="Select"
                                :items="['CBD', 'Madaraka', 'Westlands', 'Buruburu']"
                                variant="outlined"
                            ></v-select>
                        </v-col>
                    </v-row>
                    <v-row>                 
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Phone Number</div>
                        </v-col>
                        <v-col md="6">
                            <v-text-field type="number" v-model="phone" variant="outlined"></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>                 
                        <v-col md="6">
                            <div class="text-title-large font-weight-medium text-right">Gender</div>
                        </v-col>
                        <v-col md="6">
                            <v-radio-group v-model="gender" inline>
                                <v-radio label="Male" value="male"></v-radio>
                                <v-radio label="Female" value="female"></v-radio>
                            </v-radio-group>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <v-btn color="#3A4B68" variant="elevated" @click='signUp'>Sign Up</v-btn>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="12">
                            <div>New to MacFit?  Create an account</div>
                        </v-col>
                    </v-row>
                </v-form>
            </v-col>
        </v-row>
    </v-container>

</template>