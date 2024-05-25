<template>
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          <q-avatar>
            <img src="https://i.pinimg.com/564x/27/a7/43/27a743d54b2dd5a52df2e0addbfd433f.jpg">
          </q-avatar>
          Alif Sepatu Jordan
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
  </template>
  
  <script>
  export default {
    props: {
      toggleLeftDrawer: Function,
      toggleRightDrawer: Function
    }
  }
  </script>
  
  <style scoped>
  /* Add your scoped styles here */
  </style>
  