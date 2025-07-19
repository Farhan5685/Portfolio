<template>
    <v-container class="py-16">
      <!-- Heading -->
      <h2 class="text-h4 font-weight-bold text-center mb-12 animate__animated animate__fadeInDown">
        Let's Connect
      </h2>
  
      <v-row align="stretch" class="animate__animated animate__fadeInUp">
        <!-- LEFT: Social Links in a Row -->
        <v-col cols="12" md="5" class="d-flex align-center justify-center">
          <div class="d-flex flex-wrap justify-center gap-6">
            <v-tooltip text="WhatsApp" location="top">
              <template #activator="{ props }">
                <v-btn
                  v-bind="props"
                  icon
                  size="x-large"
                  color="green"
                  href="https://wa.me/923166570343"
                  target="_blank"
                >
                  <v-icon size="36">mdi-whatsapp</v-icon>
                </v-btn>
              </template>
            </v-tooltip>
  
            <v-tooltip text="GitHub" location="top">
              <template #activator="{ props }">
                <v-btn
                  v-bind="props"
                  icon
                  size="x-large"
                  color="blue"
                  href="https://github.com/farhanhussain"
                  target="_blank"
                >
                  <v-icon size="36">mdi-github</v-icon>
                </v-btn>
              </template>
            </v-tooltip>
  
            <v-tooltip text="Email" location="top">
              <template #activator="{ props }">
                <v-btn
                  v-bind="props"
                  icon
                  size="x-large"
                  color="red"
                  href="mailto:farhan@email.com"
                  target="_blank"
                >
                  <v-icon size="36">mdi-email</v-icon>
                </v-btn>
              </template>
            </v-tooltip>
          </div>
        </v-col>
  
        <!-- RIGHT: Contact Form -->
        <v-col cols="12" md="7">
          <v-card
            elevation="6"
            :class="[dark ? 'bg-dark' : 'bg-light']"
            class="pa-6"
          >
            <v-form ref="formRef" v-model="valid">
              <v-text-field
                v-model="form.name"
                label="Name"
                variant="outlined"
                :rules="[v => !!v || 'Name is required']"
                class="mb-4"
                clearable
                required
              />
  
              <v-text-field
                v-model="form.email"
                label="Email"
                type="email"
                variant="outlined"
                :rules="[v => !!v || 'Email is required']"
                class="mb-4"
                clearable
                required
              />
  
              <v-textarea
                v-model="form.message"
                label="Message"
                variant="outlined"
                rows="5"
                auto-grow
                :rules="[v => !!v || 'Message is required']"
                class="mb-4"
                clearable
                required
              />
  
              <v-btn
                color="primary"
                size="large"
                block
                @click="submitForm"
              >
                Send Message
              </v-btn>
            </v-form>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  import { useTheme } from 'vuetify'
  
  const theme = useTheme()
  const dark = computed(() => theme.global.current.value.dark)
  
  const valid = ref(false)
  const formRef = ref()
  const form = ref({
    name: '',
    email: '',
    message: ''
  })
  
  function submitForm() {
    if (formRef.value?.validate()) {
      alert(`Thanks ${form.value.name}! I'll contact you shortly.`)
      form.value = { name: '', email: '', message: '' }
      formRef.value.resetValidation()
    }
  }
  </script>
  
  <style scoped>
  @import 'animate.css';
  
  .bg-dark {
    background-color: #1e1e1e;
    color: #fff;
  }
  .bg-light {
    background-color: #ffffff;
    color: #000;
  }
  .gap-6 {
    gap: 24px;
  }
  </style>
  