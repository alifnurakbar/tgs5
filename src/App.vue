<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          <q-avatar>
            <img src="https://i.pinimg.com/564x/27/a7/43/27a743d54b2dd5a52df2e0addbfd433f.jpg">
          </q-avatar>
           Sepatu Jordan
        </q-toolbar-title>
        <q-btn dense flat round icon="shopping_cart" @click="toggleRightDrawer" />
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/page1" label="Home" />
        <q-route-tab to="/page2" label="Products" />
        <q-route-tab to="/page3" label="About Us" />
        <q-route-tab to="/page4" label="Contact" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <q-list>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            Home
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="category" />
          </q-item-section>
          <q-item-section>
            Categories
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="info" />
          </q-item-section>
          <q-item-section>
            About Us
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="contact_mail" />
          </q-item-section>
          <q-item-section>
            Contact
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
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
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md">
        <q-carousel animated v-model="slide" arrows navigation infinite>
          <q-carousel-slide v-for="slide in slides" :key="slide.name" :name="slide.name" :img-src="slide.imgSrc" />
        </q-carousel>
      </div>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Toko Alif Sepatu Jordan
        </q-toolbar-title>
        <div>© 2024 Alif Sepatu Jordan. All rights reserved.</div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)
    const slide = ref(1)
    const lorem = ref("Lorem ipsum dolor sit amet, consectetur adipiscing elit.")
    const cartItems = ref([
      { id: 1, name: 'Sepatu Jordan 1', price: 'Rp 5.500.000', imgSrc: 'https://i.pinimg.com/564x/4e/a3/2b/4ea32bde3d6d10178cfab2186713402c.jpg' },
      { id: 2, name: 'Sepatu Jordan 2', price: 'Rp 7.200.000', imgSrc: 'https://i.pinimg.com/564x/78/a2/a6/78a2a6348ca885c34c04465c49502d2e.jpg' },
      // Add more items as needed
    ])
    const slides = ref([
      { name: 1, imgSrc: 'https://edit.voila.id/wp-content/uploads/nc/articles/Rekomendasi-Sepatu-Air-Jordan-yang-Harus-Kamu-Miliki.jpg' },
      { name: 2, imgSrc: 'https://asset-2.tstatic.net/pontianak/foto/bank/images/air-jordan-1-retro-high_20180706_113954.jpg' },
      { name: 3, imgSrc: 'https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full/catalog-image/MTA-152777414/nike_nike_men_basketball_air_jordan_xxxviii_rui_pf_sepatu_basket_pria_-fd0583-003-_full03_rbdiposh.jpeg' },
      { name: 4, imgSrc: 'https://hardrockfm.com/wp-content/uploads/2022/04/Sederet-Sneakers-Air-Jordan-yang-Rilis-Bulan-April-2022-10.webp' }
    ])

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value
    }

    const removeFromCart = (id) => {
      cartItems.value = cartItems.value.filter(item => item.id !== id)
    }

    return {
      leftDrawerOpen,
      rightDrawerOpen,
      slide,
      lorem,
      cartItems,
      slides,
      toggleLeftDrawer,
      toggleRightDrawer,
      removeFromCart
    }
  }
}
</script>

<style>
.my-card {
  width: 300px;
  max-width: 100%;
}

.q-header, .q-footer {
  background: linear-gradient(45deg, #1e3c72 0%, #2a5298 100%);
}

.q-drawer {
  background-color: #f8f9fa;
}

.q-carousel-slide img {
  object-fit: cover;
  height: 100%;
}

.q-toolbar-title .q-avatar img {
  border-radius: 50%;
}

.q-toolbar-title div {
  font-size: 1.5rem;
  font-weight: bold;
  margin-left: 1rem;
}

.q-footer {
  text-align: center;
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
