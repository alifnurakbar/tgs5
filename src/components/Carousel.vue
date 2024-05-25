<template>
    <q-page-container>
      <div class="q-pa-md">
        <q-carousel animated v-model="slide" arrows navigation infinite>
          <q-carousel-slide v-for="slide in slides" :key="slide.name" :name="slide.name" :img-src="slide.imgSrc" />
        </q-carousel>
      </div>
    </q-page-container>
  </template>
  
  <script>
  export default {
    props: {
      slides: Array
    },
    data() {
      return {
        slide: 1
      };
    }
  }
  </script>
  