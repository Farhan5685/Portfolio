<template>
    <v-footer :class="[dark ? 'footer-dark' : 'footer-light']" class="py-12 px-6">
      <v-container>
        <v-row>
          <!-- Left Side: Branding -->
          <v-col cols="12" md="6" class="mb-6 mb-md-0">
            <h3 class="text-h5 font-weight-bold" :class="dark ? 'text-white' : 'text-primary'">
              Farhan<span style="color: #00bcd4">.Dev</span>
            </h3>
            <p class="mt-2 text-subtitle-2">
              Turning ideas into clean, modern, responsive apps using Vue 3 & Vuetify.
            </p>
            <p class="mt-4 text-caption">&copy; {{ new Date().getFullYear() }} Farhan Hussain. All rights reserved.</p>
          </v-col>
  
          <!-- Right Side: Sexy Hover Switch Buttons -->
          <v-col cols="12" md="6" class="d-flex justify-center justify-md-end gap-6 flex-wrap">
            <div
              v-for="link in links"
              :key="link.name"
              class="circle-hover"
            >
              <a :href="link.url" target="_blank" class="circle-content">
                <v-icon class="icon">{{ link.icon }}</v-icon>
                <span class="text">{{ link.name }}</span>
              </a>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>
  </template>
  
  <script setup>
  import { computed } from 'vue'
  import { useTheme } from 'vuetify'
  
  const theme = useTheme()
  const dark = computed(() => theme.global.current.value.dark)
  
  const links = [
    {
      name: 'WhatsApp',
      icon: 'mdi-whatsapp',
      url: 'https://wa.me/923166570343',
    },
    {
      name: 'GitHub',
      icon: 'mdi-github',
      url: 'https://github.com/farhanhussain',
    },
    {
      name: 'Email',
      icon: 'mdi-email',
      url: 'mailto:farhan@email.com',
    }
  ]
  </script>
  
  <style scoped>
  .footer-light {
    background-color: #f4f4f4;
    color: #000;
  }
  .footer-dark {
    background-color: #121212;
    color: #fff;
  }
  .gap-6 {
    gap: 24px;
  }
  
  .circle-hover {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background-color: #00bcd4;
    position: relative;
    overflow: hidden;
    transition: background-color 0.3s ease;
  }
  
  .circle-hover:hover {
    background-color: #008ba3;
  }
  
  .circle-content {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    text-decoration: none;
    color: white;
    font-weight: bold;
    overflow: hidden;
  }
  
  .icon,
  .text {
    position: absolute;
    transition: transform 0.4s ease, opacity 0.4s ease;
  }
  
  .icon {
    transform: translateY(0);
    opacity: 1;
  }
  
  .text {
    transform: translateY(100%);
    opacity: 0;
    font-size: 13px;
  }
  
  .circle-hover:hover .icon {
    transform: translateY(-100%);
    opacity: 0;
  }
  
  .circle-hover:hover .text {
    transform: translateY(0);
    opacity: 1;
  }
  </style>
  