<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="left = !left"  class="q-drawer-button"/>

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Demo
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer 
      :breakpoint="767"
      :width="250"
     v-model="left"
      side="left" bordered
     >
      <!-- drawer content -->
      <q-list bordered>
      <q-item 
      v-for="nav in navs"
      :key="nav.label"
      :to="nav.to"
      
      exact
      class="q-drawer-ins"
      
      clickable v-ripple>
        <q-item-section avatar>
          <q-icon color="primary" :name="nav.icon" />
        </q-item-section>

        <q-item-section>  <q-item-label>{{ nav.label }}</q-item-label></q-item-section>
      </q-item>

     </q-list>

             
   
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { openURL } from 'quasar'
export default {
  data () {
    return {
      left: this.$q.platform.is.desktop,
              navs: [
          {
            label: 'Inventory',
            icon: 'list',
            to: '/'
          },
          {
            label: 'Settings',
            icon: 'settings',
            to: '/settings'
          }
        ]
    }
  },
     methods: {
      openURL
    }
}
</script>

<style lang="scss">
  @media screen and (min-width: 768px) {
    .q-drawer-button {
      display: none;
    }
  }
  
  .q-drawer {
    .q-router-link--exact-active {
      color: grey !important;
    }
  }

 </style>