<template>
    <!-- App Bar -->
    <v-app-bar
      app
      flat
      class="glass-navbar"
      :elevation="scrolling ? 4 : 0"
    >
      <v-container class="d-flex justify-space-between align-center">
        <!-- Logo -->
        <h2
          class="font-weight-bold text-h5"
          :class="dark ? 'text-white' : 'text-primary'"
          style="font-family: 'Courier New', monospace"
        >
          Farhan<span style="color:#00bcd4">.Dev</span>
        </h2>
  
        <!-- Desktop Nav Links -->
        <v-btn-toggle class="d-none d-sm-flex" divided>
          <v-btn to="/" variant="text">Home</v-btn>
          <v-btn to="/about" variant="text">About</v-btn>
          <v-btn to="/projects" variant="text">Projects</v-btn>
          <v-btn to="/contact" variant="text">Contact</v-btn>
        </v-btn-toggle>
  
        <!-- Actions -->
        <div class="d-flex align-center gap-2">
          <!-- Dark Mode Toggle -->
          <v-btn icon @click="toggleTheme">
            <v-icon>{{ dark ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent' }}</v-icon>
          </v-btn>
  
          <!-- WhatsApp Button (icon on small screens) -->
          <v-btn
            :icon="$vuetify.display.smAndDown"
            color="green"
            href="https://wa.me/923166570343"
            target="_blank"
            variant="flat"
          >
            <v-icon start>mdi-whatsapp</v-icon>
            <span v-if="$vuetify.display.mdAndUp">WhatsApp</span>
          </v-btn>
  
          <!-- Hamburger icon on mobile -->
          <v-app-bar-nav-icon
            class="d-sm-none"
            @click="drawer = true"
          />
        </div>
      </v-container>
    </v-app-bar>
  
    <!-- Navigation Drawer (Mobile Only) -->
    <v-navigation-drawer
      v-model="drawer"
      temporary
      location="right"
      class="d-sm-none"
    >
    <v-list nav dense>
  <v-list-item v-for="item in menuItems" :key="item.title" :to="item.to" link>
    <v-list-item-title>{{ item.title }}</v-list-item-title>
  </v-list-item>
</v-list>

    </v-navigation-drawer>
  </template>
  
  <script setup>
  import { useTheme } from 'vuetify'
  import { computed, ref, onMounted, onUnmounted } from 'vue'
  
  const theme = useTheme()
  const dark = computed(() => theme.global.current.value.dark)
  const drawer = ref(false)
  
  function toggleTheme() {
    theme.global.name.value = dark.value ? 'light' : 'dark'
  }
  const menuItems = [
  { title: "Home", to: "/" },
  { title: "About", to: "/about" },
  { title: "Projects", to: "/projects" },
  { title: "Contact", to: "/contact" },
]
  
  // Blur + shadow on scroll
  const scrolling = ref(false)
  const handleScroll = () => {
    scrolling.value = window.scrollY > 10
  }
  onMounted(() => window.addEventListener('scroll', handleScroll))
  onUnmounted(() => window.removeEventListener('scroll', handleScroll))
  </script>
  
  <style scoped>
  .gap-2 {
    gap: 8px;
  }
  
  .glass-navbar {
    backdrop-filter: blur(12px);
    background-color: rgba(255, 255, 255, 0.08);
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    transition: background-color 0.3s, box-shadow 0.3s;
  }
  
  body.dark .glass-navbar {
    background-color: rgba(18, 18, 18, 0.5);
  }
  </style>
  