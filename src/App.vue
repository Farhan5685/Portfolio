<template>
  <v-app>
    <Navbar />
    <LightingCursor />
    <v-main>
      <router-view />
    </v-main>
    <FooterSection />
  </v-app>
</template>

<script setup>
import Navbar from '@/components/Navbar.vue'
import FooterSection from '@/components/FooterSection.vue'
import LightingCursor from '@/components/LightingCursor.vue'
</script>
