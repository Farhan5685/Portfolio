<template>
    <v-container class="fill-height d-flex align-center justify-center">
      <v-row class="text-center" justify="center">
        <v-col cols="12" md="8">
          <!-- Name -->
          <h1 class="text-h3 font-weight-bold mb-4 fade-in">
            Hi, I’m <span class="text-primary">Farhan Hussain</span>
          </h1>
  
          <!-- Animated Title -->
          <h2 class="text-h5 mb-4 slide-up animate-text">
            {{ titles[currentTitleIndex] }}
          </h2>
  
          <!-- Bio -->
          <p class="text-body-1 mb-6 fade-in delay-1">
            I’m a passionate frontend developer crafting modern interfaces using Vue 3 and Vuetify with love and perfection.
          </p>
  
          <!-- CTA Button -->
          <v-btn
            color="primary"
            size="large"
            class="fade-in delay-2"
            href="https://wa.me/923166570343"
            target="_blank"
          >
            Hire Me
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  
  const titles = [
    'Frontend Developer',
    'Vue.js Specialist',
    'Clean UI Coder',
    'Perfect'
  ]
  
  const currentTitleIndex = ref(0)
  
  onMounted(() => {
    setInterval(() => {
      currentTitleIndex.value = (currentTitleIndex.value + 1) % titles.length
    }, 2500)
  })
  </script>
  
  <style scoped>
  .fill-height {
    min-height: 100vh;
  }
  
  .fade-in {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeIn 1s ease-out forwards;
  }
  
  .fade-in.delay-1 {
    animation-delay: 0.5s;
  }
  .fade-in.delay-2 {
    animation-delay: 1s;
  }
  
  @keyframes fadeIn {
    to {
      opacity: 1;
      transform: none;
    }
  }
  
  .slide-up {
    animation: slideUp 0.8s ease-out forwards;
  }
  
  @keyframes slideUp {
    from {
      transform: translateY(20px);
      opacity: 0;
    }
    to {
      transform: translateY(0px);
      opacity: 1;
    }
  }
  
  .animate-text {
    color: #00bcd4;
    transition: all 0.3s ease;
  }
  </style>
  