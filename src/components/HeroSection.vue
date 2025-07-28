<template>
  <v-container class="hero-wrapper" fluid>
    <!-- HERO SECTION (100vh) -->
    <v-row class="text-center" justify="center" align="center" style="height: 100vh">
      <v-col cols="12" md="8">
        <h1 class="text-h3 font-weight-bold mb-4 fade-in">
          Hi, I’m <span class="text-primary">Farhan Hussain</span>
        </h1>

        <h2 class="text-h5 mb-4 slide-up animate-text">
          {{ titles[currentTitleIndex] }}
        </h2>

        <p class="text-body-1 mb-6 fade-in delay-1">
          I’m a passionate frontend developer crafting modern interfaces using Vue 3 and Vuetify with love and perfection.
        </p>

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

    <!-- SERVICES SECTION (100vh) -->
    <v-row justify="center" class="text-center scroll-section py-16" style="min-height: 100vh">
      <v-col cols="12">
        <h2 class="text-h4 font-weight-bold mb-2 fade-in">My Services</h2>
        <div class="underline mx-auto mb-10"></div>
      </v-col>

      <v-col
        v-for="(service, i) in services"
        :key="i"
        cols="12"
        sm="6"
        md="4"
        class="fade-in-on-scroll d-flex"
      >
        <v-hover v-slot="{ isHovering, props }">
          <v-card
            v-bind="props"
            class="pa-6 text-center transition flex-grow-1"
            elevation="6"
            :class="{ 'hovered-card': isHovering }"
          >
            <v-icon justify="center" color="primary" size="50" class="mb-4 ">{{ service.icon }}</v-icon>
            <h3 class="text-h6 font-weight-bold mb-2">{{ service.title }}</h3>
            <p class="text-body-2">{{ service.description }}</p>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>

    <!-- TIMELINE SECTION -->
    <v-row justify="center" class="py-16 scroll-section fade-in-on-scroll">
      <v-col cols="12" md="8">
        <h2 class="text-h4 font-weight-bold mb-6 text-center">Timeline</h2>
     
        <v-timeline align="start" side="end" line-inset="8" density="compact">
          <v-timeline-item
            v-for="(event, i) in timeline"
            :key="i"
            :dot-color="event.color"
            fill-dot
          >
            <template #opposite>
              <strong>{{ event.year }}</strong>
            </template>
            <v-card elevation="3" class="pa-4">
              <h3 class="text-subtitle-1 font-weight-bold mb-2">{{ event.title }}</h3>
              <p class="text-body-2">{{ event.description }}</p>
            </v-card>
          </v-timeline-item>
        </v-timeline>
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

  // Animate on scroll
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('scroll-visible')
      }
    })
  }, { threshold: 0.1 })

  document.querySelectorAll('.fade-in-on-scroll').forEach(el => observer.observe(el))
})

const services = [
  {
    title: 'Frontend Developer',
    description:
      'Craft responsive, accessible, and pixel-perfect user interfaces using Vue 3, Vuetify, HTML, and CSS.',
    icon: 'mdi-laptop'
  },
  {
    title: 'Single Page Applications (SPA)',
    description:
      'Build dynamic, fast-loading Vue apps with Vue Router, Pinia, reusable components and real-time UI.',
    icon: 'mdi-application'
  },
  {
    title: 'Design to Code',
    description:
      'Convert Figma, PSD, or XD designs into responsive Vue 3 apps using HTML, CSS, and Vuetify.',
    icon: 'mdi-palette'
  }
]

const timeline = [
  {
    year: '2023',
    title: 'Started Frontend Journey',
    description: 'Began learning HTML, CSS, JavaScript, and diving into Vue 3 and Vuetify.',
    color: 'cyan-darken-2'
  },
  {
    year: '2024',
    title: 'Built Real Projects',
    description: 'Completed multiple real-world apps including weather, dashboard, and Netflix clone.',
    color: 'deep-purple-darken-2'
  },
  {
    year: '2025',
    title: 'Portfolio & Client Work',
    description: 'Created a beautiful portfolio and started working with clients on Fiverr & GitHub.',
    color: 'green-darken-2'
  }
]
</script>

<style scoped>
.hero-wrapper {
  scroll-behavior: smooth;
  overflow-x: hidden;
}

/* Animations */
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

/* Scroll Animation */
.fade-in-on-scroll {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.6s ease;
}
.fade-in-on-scroll.scroll-visible {
  opacity: 1;
  transform: translateY(0);
}

/* Underline */
.underline {
  width: 80px;
  height: 4px;
  background: #00bcd4;
  border-radius: 4px;
  animation: pulse 1.5s ease-in-out infinite;
  text-overflow:hidden;
}
@keyframes pulse {
  0% {
    width: 60px;
    opacity: 0.7;
  }
  50% {
    width: 80px;
    opacity: 1;
  }
  100% {
    width: 60px;
    opacity: 0.7;
  }
}

/* Card */
.transition {
  transition: all 0.3s ease;
  border-radius: 14px;
  display: flex;
  flex-direction: column;
  height: 100%;
}
.hovered-card {
  transform: translateY(-6px);
  box-shadow: 0 10px 20px rgba(0, 188, 212, 0.3);
}
</style>
