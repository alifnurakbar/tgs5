<template>
    <q-page-container>
      <div class="q-pa-md">
        <div class="q-pa-md row items-start q-gutter-md">
          <q-card v-for="item in cartItems" :key="item.id" class="my-card">
            <q-img :src="item.imgSrc">
              <div class="absolute-bottom text-h6 text-white text-center bg-black bg-opacity-50 q-pa-xs">
                {{ item.price }}
              </div>
            </q-img>
            <q-card-section>
              <div class="text-subtitle1">{{ item.name }}</div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn dense flat icon="remove_circle" @click="removeFromCart(item.id)" />
            </q-card-actions>
          </q-card>
        </div>
      </div>
    </q-page-container>
  </template>
  
  <script>
  export default {
    props: {
      cartItems: Array,
      removeFromCart: Function
    }
  }
  </script>
  
  <style scoped>
  .my-card {
    width: 300px;
    max-width: 100%;
  }
  .text-h6 {
    font-size: 1.25rem;
    font-weight: bold;
  }
  .text-subtitle1 {
    font-size: 1rem;
    font-weight: normal;
  }
  </style>
  