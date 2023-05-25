<template>
  <v-app id="inspire">
      <Header/>
      <Footer/>
    <v-main>
      <v-container>
        <RouterView />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';


</script>
