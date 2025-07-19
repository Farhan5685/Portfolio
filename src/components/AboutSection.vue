<template>
    <v-container fluid :class="['about-section', isDark ? 'bg-dark' : 'bg-light']" class="fill-height ">
      <v-row justify="center" align="center" class="text-center mb-8">
        <!-- Avatar -->
        <v-col cols="12">
          <v-avatar size="140" class="mx-auto mb-4">
            <v-img :src="farhanImage" alt="Farhan Hussain" cover />
          </v-avatar>
          <h2 class="text-h4 font-weight-bold text-primary mb-2">Farhan Hussain</h2>
          <p class="text-subtitle-1">
            Frontend Developer • Vue 3 • Vuetify • Perfectionist UI Coder
          </p>
        </v-col>
      </v-row>
  
      <!-- Bio -->
      <v-row justify="center">
        <v-col cols="12" md="8">
          <p class="text-body-1 mb-6">
            I’m a frontend developer passionate about building modern, responsive, and fast-loading web interfaces using Vue 3 and Vuetify.
            I enjoy solving UI challenges, building reusable components, and crafting clean code.
            I specialize in single-page apps, dashboards, multi-step forms, and client-ready sites.
          </p>
        </v-col>
      </v-row>
  
      <!-- Skills -->
      <v-row justify="center" class="mb-12">
        <v-col cols="12">
          <h3 class="text-h5 font-weight-bold text-primary text-center mb-6">Tech Stack & Skills</h3>
          <v-row justify="center" align="center">
            <v-col
              v-for="skill in skills"
              :key="skill.name"
              cols="6"
              sm="4"
              md="3"
              class="d-flex justify-center mb-4"
            >
              <v-card class="pa-3 text-center skill-card" flat rounded>
                <v-icon size="40" class="mb-2">{{ skill.icon }}</v-icon>
                <p class="text-subtitle-2 font-weight-medium">{{ skill.name }}</p>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
  
      <!-- Timeline -->
      <v-row justify="center">
        <v-col cols="12" md="8">
          <h3 class="text-h5 font-weight-bold text-primary text-center mb-4">Experience</h3>
          <v-timeline align="start">
            <!-- Freelancer -->
            <v-timeline-item dot-color="green" size="small">
              <template #opposite>
                <strong>2025 - Present</strong>
              </template>
              <div>
                <strong>Remote Freelancer</strong>
                <div>Helping clients worldwide with Vue 3 web apps, responsive layouts, and fixing UI/UX issues with precision.</div>
              </div>
            </v-timeline-item>
  
            <!-- Dynmix -->
            <v-timeline-item dot-color="primary" size="small">
              <template #opposite>
                <strong>2024 - 2025</strong>
              </template>
              <div>
                <strong>Frontend Developer — Dynmix Developers</strong>
                <div>
                  Worked for 9 months on complex Vue 3 projects. Built reusable components, tackled real-world bugs, optimized UI performance,
                  and collaborated in delivering production-ready SPAs with modern architecture.
                </div>
              </div>
            </v-timeline-item>
  
            <!-- CodeAlpha -->
            <v-timeline-item dot-color="primary" size="small">
              <template #opposite>
                <strong>2024</strong>
              </template>
              <div>
                <strong>Intern — CodeAlpha</strong>
                <div>
                  Supported the development of Vue 3 pages, implemented responsive designs, and handled critical bug fixes. Delivered UI components
                  used across the platform under real project deadlines.
                </div>
              </div>
            </v-timeline-item>
          </v-timeline>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script setup>
  import { useTheme } from 'vuetify'
  import { ref, watchEffect } from 'vue'
  import farhanImage from '@/assets/farhan.jpeg'
  
  const isDark = ref(false)
  
  const theme = useTheme()
  watchEffect(() => {
    isDark.value = theme.global.current.value.dark
  })
  
  const skills = [
    { name: 'Vue 3', icon: 'mdi-vuejs' },
    { name: 'Vuetify', icon: 'mdi-alpha-v-box' },
    { name: 'HTML', icon: 'mdi-language-html5' },
    { name: 'CSS', icon: 'mdi-language-css3' },
    { name: 'JavaScript', icon: 'mdi-language-javascript' },
    { name: 'Pinia', icon: 'mdi-store' },
    { name: 'Git', icon: 'mdi-git' },
    { name: 'Firebase', icon: 'mdi-fire' },
  ]
  </script>
  
  <style scoped>
  
  .fill-height {
    min-height: 100vh;
    padding:80px
  }
  .bg-dark {
    background: linear-gradient(135deg, #111, #1e1e1e);
    color: white;
  }
  .bg-light {
    background-color: #f9f9f9;
    color: #222;
  }
  .skill-card {
    background-color: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
  }
  .skill-card:hover {
    transform: scale(1.05);
    box-shadow: 0 0 15px rgba(0, 188, 212, 0.4);
  }
  
  </style>
  