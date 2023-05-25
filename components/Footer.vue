<template>
      <v-footer app class="bg-primary text-center">
      <v-row class="mt-5">
      <v-col cols="12">
        
          <v-row align="center">
            <v-col>
              <span class="white--text">&copy; 2023 Your Company. All rights reserved.</span>
              <div class="social-icons">
              <v-icon size="24" class="mr-2">mdi-instagram</v-icon>
              <v-icon size="24" class="mr-2">mdi-facebook</v-icon>
              <v-icon size="24" class="mr-2">mdi-linkedin</v-icon>
              <v-icon size="24" class="mr-2">mdi-twitter</v-icon>
              
              <!-- Ajoutez d'autres icônes ici -->
            </div>
            </v-col>
          </v-row>
       
      </v-col>
    </v-row>
</v-footer>
  </template>
  
  <script>
  export default {
    name: 'Footer',
  }
  </script>
  
  <style scoped>
  .social-icons {
    display: flex;
    align-items: center;
  }

  </style>
  