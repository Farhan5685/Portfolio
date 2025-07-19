<template>
  <v-container class="pro">
    <h2 class="text-h4 font-weight-bold mb-8 text-center">My Projects</h2>

    <v-row dense>
      <v-col
        v-for="(project, index) in projects"
        :key="index"
        cols="12"
        sm="6"
        md="6"
      >
        <v-hover v-slot="{ isHovering, props }">
          <v-card
            elevation="6"
            class="project-card transition-fast-in-fast-out"
            v-bind="props"
          >
            <v-img :src="project.image" height="180" cover />

            <v-card-title class="font-weight-bold text-primary">
              {{ project.title }}
            </v-card-title>

            <v-card-text>
              <p>{{ project.description }}</p>
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

            <v-expand-transition>
              <div v-if="isHovering">
                <v-card-actions class="d-flex justify-space-between px-4 pb-4">
                  <v-btn
                    v-if="project.demo"
                    :href="project.demo"
                    target="_blank"
                    color="cyan-darken-2"
                    variant="flat"
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
              </div>
            </v-expand-transition>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
const projects = [
  {
    title: "Admin Dashboard",
    description:
      "A modern admin panel with theme toggle, CRUD users, charts, and protected routes. Built with Vue 3 + Vuetify + Pinia.",
    image: new URL('@/assets/admindashboard.PNG', import.meta.url).href,
    tech: ["Vue 3", "Vuetify", "Pinia", "Chart.js"],
    demo: "https://admindashboard-farhan5685s-projects.vercel.app",
    github: "https://github.com/Farhan5685/AdminDashboard",
  },
  {
    title: "Weather App",
    description:
      "Simple but beautiful weather app with OpenWeatherMap API, using Vuetify and Vue. Mobile responsive UI.",
    image: new URL('@/assets/Weather.PNG', import.meta.url).href,
    tech: ["Vue", "API", "Vuetify"],
    demo: "https://weather-by-farhan.vercel.app/",
    github: "https://github.com/Farhan5685/WeatherByFarhan",
  },
];
</script>

<style scoped>
.pro {
  padding-top: 90px;
}
.project-card {
  transition: transform 0.3s, box-shadow 0.3s;
}
.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 188, 212, 0.3);
}
</style>
