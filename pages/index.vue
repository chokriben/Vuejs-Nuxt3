<template>
    <div>
      <v-row class="my-5">
        <v-col cols="12">
          <v-btn @click="grid = !grid" :class="{ 'bg-primary': grid }">
            <v-icon> mdi-view-list </v-icon>
          </v-btn>
          <v-btn
            @click="grid = !grid"
            :class="{ 'bg-primary': !grid }"
            class="ml-3"
          >
            <v-icon> mdi-apps </v-icon>
          </v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-row v-show="grid">
            <v-col
              v-for="(product, i) in products"
              :key="i"
              cols="12"
              lg="4"
              sm="6"
            >
              <v-card class="mx-auto pb-2">
                <v-img :src="product.image" height="280px" width="220px" cover>
                  <template v-slot:placeholder>
                    <v-row
                      align="center"
                      class="fill-height ma-0"
                      justify="center"
                    >
                      <v-progress-circular
                        color="grey lighten-5"
                        indeterminate
                      ></v-progress-circular>
                    </v-row>
                  </template>
                </v-img>
  
                <v-card-title class="text-capitalize">
                  {{ product.name }}
                </v-card-title>
  
                <v-card-subtitle> ${{ product.price }} </v-card-subtitle>
                <v-card-actions>
                  <v-btn color="primary" @click="afficherPlus(product.id)">Read More</v-btn>
                   <div v-if="produitSupplementaire">
                   <!-- Détails du produit supplémentaire à afficher -->
                            
                    <p>{{ produitSupplementaire.description }}</p>
                     <!-- Autres détails du produit -->
                         </div>
                  <v-spacer></v-spacer>
                  <v-btn class="bg-primary" @click="cartStore.add(product.id)">
                    Add to Cart
                  </v-btn>
                  <!-- <v-btn class="bg-primary"> Add to Cart </v-btn> -->
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
          <v-row v-show="!grid" v-for="(product, i) in products" :key="i">
            <v-col cols="4">
              <v-img :src="product.image" height="280px" width="220px" cover>
                <template v-slot:placeholder>
                  <v-row align="center" class="fill-height ma-0" justify="center">
                    <v-progress-circular
                      color="grey lighten-5"
                      indeterminate
                    ></v-progress-circular>
                  </v-row>
                </template>
              </v-img>
            </v-col>
            <v-col cols="12" md="8">
              <v-card-title class="text-capitalize">
                {{ product.name }}
              </v-card-title>
  
              <v-card-subtitle> ${{ product.price }} </v-card-subtitle>
              <v-card-text>
                {{ product.description }}
              </v-card-text>
              <v-card-actions>
                <v-btn color="primary"> Read More </v-btn>
                <v-btn class="ml-2 bg-primary" @click="cartStore.add(product.id)">
                  Add to Cart
                </v-btn>
              </v-card-actions>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </div>
    <!-- <div>
      <v-row class="mt-5">
      <v-col cols="12">
        <v-footer class="bg-primary text-center">
          <v-row align="center">
            <v-col>
              <span class="white--text">&copy; 2023 Your Company. All rights reserved.</span>
            </v-col>
          </v-row>
        </v-footer>
      </v-col>
    </v-row>
    </div> -->
  </template>
  
  <script setup>
import { ref } from 'vue';
import data from "../data";
import { useCartStore } from '../stores/cart.js'

const cartStore = useCartStore();
const products = ref(data);
const grid = ref(true);
const produitSupplementaire = ref(null);

function afficherPlus(productId) {
  produitSupplementaire.value = products.value.find(product => product.id === productId);
}
</script>
  
  <style lang="scss" scoped>
  </style>