<template>
  <q-layout view="lHh Lpr lFf">
    <q-header style="color: #03363d; background-color: #ffffff;" elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title style="display: flex; align-items: center;">
          <img
            src="https://static.zdassets.com/sunco-accounts/sunco-dashboard/v39/images/sunco_logof8b8a1d73d5a85009f61.svg"
            alt="Smooch Logo"
            style="height: 24px; margin-right: 8px;"
          />
           | <span class="text-bold q-ml-sm text-subtitle1">Smooch Utils</span>
        </q-toolbar-title>

        <div class="gt-xs">by: <span class="text-bold">Enzadaz</span></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          MENU
        </q-item-label>

        <EssentialLink
        class="color-smooch"
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Home',
    caption: 'Start',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Token Generator',
    caption: 'Jwt',
    icon: 'token',
    link: 'token-generator'
  },

]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
