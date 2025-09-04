<template>
  <v-container class="pro">
    <h2 class="text-h4 font-weight-bold mb-8 text-center">My Projects</h2>

    <!-- Category Filters -->
    <div class="d-flex justify-center mb-6">
      <v-btn
        v-for="cat in categories"
        :key="cat"
        :variant="selectedCategory === cat ? 'flat' : 'outlined'"
        color="primary"
        class="ma-2"
        @click="selectedCategory = cat"
      >
        {{ cat }}
      </v-btn>
    </div>

    <!-- Project Cards -->
    <v-row dense>
      <v-col
        v-for="(project, index) in filteredProjects"
        :key="index"
        cols="12"
        sm="6"
        md="4"
      >
        <div
          class="project-3d"
          @mousemove="handleMouseMove($event, index)"
          @mouseleave="resetTilt(index)"
          :style="tiltStyles[index]"
        >
          <v-card
            elevation="6"
            class="project-card"
            style="background-color: #1e1e1e; color: #fff;"
          >
            <v-img :src="project.image" height="180" cover />

            <v-card-title class="font-weight-bold text-primary">
              {{ project.title }}
            </v-card-title>

            <v-card-text>
              <p style="color: #ccc;">{{ project.description }}</p>
              <div class="mt-2">
                <v-chip
                  v-for="(tech, i) in project.tech"
                  :key="i"
                  size="small"
                  class="ma-1"
                  color="primary"
                  variant="elevated"
                >
                  {{ tech }}
                </v-chip>
              </div>
            </v-card-text>

            <v-card-actions class="d-flex justify-start px-4 pb-4">
              <v-btn
                v-if="project.demo"
                :href="project.demo"
                target="_blank"
                color="cyan-darken-2"
                variant="flat"
                class="me-2"
              >
                Live Demo
              </v-btn>
              <v-btn
                v-if="project.github"
                :href="project.github"
                target="_blank"
                variant="outlined"
                color="primary"
              >
                GitHub
              </v-btn>
            </v-card-actions>
          </v-card>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, computed, reactive } from "vue";

const categories = ["All", "Web Apps", "Dashboards", "API"];
const selectedCategory = ref("All");

const projects = [
  {
    title: "E-Commerce",
    description:
      "Step into a world of exquisite traditional and modern clothing. Each piece tells a story of timeless beauty.",
    image: new URL("@/assets/Store.jpg", import.meta.url).href,
    tech: ["Tailwind", "Cart", "JavaScript"],
    demo: "https://farhan5685.github.io/MyStore/",
    github: "https://github.com/Farhan5685/AdminDashboard",
    category: "Web Apps",
  },
  {
    title: "Admin Dashboard",
    description:
      "A modern admin panel with theme toggle, CRUD users, charts, and protected routes. Built with Vue 3 + Vuetify + Pinia.",
    image: new URL("@/assets/admindashboard.PNG", import.meta.url).href,
    tech: ["Vue 3", "Vuetify", "Pinia", "Chart.js"],
    demo: "https://admin-dashboard-farhan-5cv1.vercel.app/",
    github: "https://github.com/Farhan5685/AdminDashboard",
    category: "Dashboards",
  },
  {
    title: "Weather App",
    description:
      "Simple but beautiful weather app with OpenWeatherMap API, using Vuetify and Vue. Mobile responsive UI.",
    image: new URL("@/assets/Weather.PNG", import.meta.url).href,
    tech: ["Vue", "API", "Vuetify"],
    demo: "https://weather-by-farhan.vercel.app/",
    github: "https://github.com/Farhan5685/WeatherByFarhan",
    category: "API",
  },
];

const filteredProjects = computed(() => {
  if (selectedCategory.value === "All") return projects;
  return projects.filter((p) => p.category === selectedCategory.value);
});

// 3D Tilt Effect
const tiltStyles = reactive({});

function handleMouseMove(event, index) {
  const card = event.currentTarget;
  const rect = card.getBoundingClientRect();
  const x = event.clientX - rect.left;
  const y = event.clientY - rect.top;
  const centerX = rect.width / 2;
  const centerY = rect.height / 2;
  const rotateX = ((y - centerY) / centerY) * 8; // tilt power
  const rotateY = ((x - centerX) / centerX) * -8;

  tiltStyles[index] = {
    transform: `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.02)`,
    transition: "transform 0.1s ease",
  };
}

function resetTilt(index) {
  tiltStyles[index] = {
    transform: "rotateX(0) rotateY(0) scale(1)",
    transition: "transform 0.5s ease",
  };
}
</script>

<style scoped>
.pro {
  padding-top: 90px;
}
.project-card {
  border-radius: 16px;
  overflow: hidden;
}
.project-3d {
  perspective: 1000px;
}
</style>
