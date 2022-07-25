<template>
  <q-layout view="lHh LpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="menu"
          class="q-mr-sm"
          @click="toggleLeftDrawer"
        />
        <q-avatar>
          <img src="~assets/logo/dark.svg" />
        </q-avatar>
        <q-toolbar-title>{{ productName }}</q-toolbar-title>

        <q-toggle
          :model-value="isDark"
          color="grey-1"
          icon-color="grey-7"
          keep-color
          checked-icon="dark_mode"
          unchecked-icon="light_mode"
          size="lg"
          @update:model-value="setDark"
        />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above side="left" bordered>
      <q-list> </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import { isDark, setDark } from '../lib/dark'

const leftDrawerOpen = ref(false)

const toggleLeftDrawer = () => {
  leftDrawerOpen.value = !leftDrawerOpen.value
}

const productName = process.env.PRODUCT_NAME
</script>
