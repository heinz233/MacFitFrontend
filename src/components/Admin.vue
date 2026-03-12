<script setup>
import { ref } from 'vue'

const users = ref([
  { id: 1, name: 'John Doe', email: 'john@example.com', gym: 'CBD', status: 'Active', bundle: 'Monthly' },
  { id: 2, name: 'Jane Smith', email: 'jane@example.com', gym: 'Westlands', status: 'Active', bundle: '3 Months' },
  { id: 3, name: 'Mike Johnson', email: 'mike@example.com', gym: 'Madaraka', status: 'Pending', bundle: 'Daily' },
  { id: 4, name: 'Sarah Wilson', email: 'sarah@example.com', gym: 'Buruburu', status: 'Active', bundle: 'Annual' }
])

const stats = ref({
  totalMembers: 1245,
  activeMembers: 1123,
  monthlyRevenue: '2.5M Ksh',
  newSignups: 45
})

const selectedUser = ref(null)
</script>

<template>
  <v-container fluid class="pa-4 pa-md-8">
    <!-- Header -->
    <v-row class="mb-8">
      <v-col cols="12">
        <div class="text-h3 mb-2">Admin Dashboard</div>
        <div class="text-subtitle-1 text-medium-emphasis">Manage members, bundles, and gym operations</div>
      </v-col>
    </v-row>

    <!-- Stats Cards -->
    <v-row class="mb-12">
      <v-col v-for="(stat, key) in stats" :key="key" cols="12" sm="6" md="3">
        <v-card class="pa-6 elevation-4 hover">
          <div class="text-h6 font-weight-medium text-medium-emphasis mb-2">{{ key.replace(/([A-Z])/g, ' $1').replace(/^./, str => str.toUpperCase()) }}</div>
          <div class="text-h4 font-weight-black primary--text">{{ typeof stat === 'number' ? stat.toLocaleString() : stat }}</div>
        </v-card>
      </v-col>
    </v-row>

    <!-- Users Table -->
    <v-card class="elevation-8">
      <v-card-title class="text-h5">
        <v-icon start size="32" color="primary">mdi-account-group</v-icon>
        Members ({{ users.length }})
      </v-card-title>
      <v-data-table
        :headers="[
          { title: 'Name', key: 'name', sortable: true },
          { title: 'Email', key: 'email' },
          { title: 'Gym Location', key: 'gym' },
          { title: 'Status', key: 'status' },
          { title: 'Bundle', key: 'bundle' },
          { title: 'Actions', key: 'actions', sortable: false }
        ]"
        :items="users"
        class="elevation-0"
        item-value="id"
        hide-default-footer
      >
        <template #item.status="{ item }">
          <v-chip 
            :color="item.status === 'Active' ? 'success' : 'warning'" 
            variant="tonal"
            size="small"
          >
            {{ item.status }}
          </v-chip>
        </template>
        <template #item.actions="{ item }">
          <v-btn 
            icon="mdi-pencil" 
            variant="text" 
            size="small" 
            @click="selectedUser = item"
            class="me-1"
          ></v-btn>
          <v-btn 
            icon="mdi-eye" 
            variant="text" 
            size="small"
          ></v-btn>
        </template>
      </v-data-table>
    </v-card>

    <!-- Quick Actions -->
    <v-row class="mt-12">
      <v-col cols="12" md="4">
        <v-card class="pa-6">
          <v-icon color="secondary" size="48" class="mb-4">mdi-account-plus</v-icon>
          <div class="text-h6 font-weight-bold mb-2">Add New Member</div>
          <v-btn color="primary" block rounded="xl">New Member</v-btn>
        </v-card>
      </v-col>
      <v-col cols="12" md="4">
        <v-card class="pa-6">
          <v-icon color="secondary" size="48" class="mb-4">mdi-package-plus</v-icon>
          <div class="text-h6 font-weight-bold mb-2">Manage Bundles</div>
          <v-btn color="primary" block rounded="xl">Manage Bundles</v-btn>
        </v-card>
      </v-col>
      <v-col cols="12" md="4">
        <v-card class="pa-6">
          <v-icon color="secondary" size="48" class="mb-4">mdi-chart-line</v-icon>
          <div class="text-h6 font-weight-bold mb-2">View Reports</div>
          <v-btn color="primary" block rounded="xl">Reports</v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

