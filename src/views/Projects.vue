<template>
    <div>
      <main class="container mx-auto px-6 py-12">
        <div class="mb-12">
          <h1 class="text-4xl font-bold text-white mb-4">My Projects</h1>
          <p class="text-gray-300 max-w-2xl">
            Here are some of my recent projects that showcase my skills in
            backend development and system architecture. Each project
            demonstrates different aspects of my technical expertise.
          </p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <ProjectCard
            v-for="(project, index) in projects"
            :key="index"
            v-bind="project"
          />
        </div>
      </main>
    </div>
  </template>
  
  <script>
  import { Download, Mail, Linkedin, Github } from 'lucide-vue-next'
  import ProjectCard from '@/assets/components/ProjectCard.vue'
  
  export default {
    name: 'App',
    components: {
      ProjectCard,
      Download,
      Mail,
      Linkedin,
      Github
    },
    data() {
      return {
        projects: [
        {
            title: "Playlist Pilot",
            description: "PlaylistPilot is an innovative AI-powered app designed to automatically create personalized Spotify playlists. It offers two unique features: the Time Machine, which lets users revisit Billboard Hot 100 hits from any date, and the AI-curated playlists, which provide a custom playlist tailored to the user’s preferences. Both features effortlessly generate playlists, providing a seamless, personalized music experience.",
            images: [
              "/images/playlistpilot1.png",
              "/images/playlistpilot2.png",
              "/images/playlistpilot3.png",
            ],
            technologies: ["Python", "Django", "Beautiful soup", "Gemini Ai", "Spotify Web Api", "Vue.js"],
            githubUrl: "https://github.com/kinging1022/playlistpilot",
            liveUrl: "#",
          },
        {
            title: "Medicare app",
            description: "An online hospital platform designed to replicate real-life consultations between patients and doctors. Patients can book appointments, chat with doctors, and make payments for consultations. Doctors can prescribe medications, which are automatically added to the patient's profile. Additionally, patients can set reminders for their medications, ensuring timely adherence to their treatment plan.",
            images: [
              "/images/medicare1.png",
              "/images/medicare2.png",
              "/images/medicare3.png",
              "/images/medicare4.png",
            ],
            technologies: ["Restframework", "Django", "Celery", 'Vue', 'websockets', 'stripe'],
            githubUrl: "https://github.com/kinging1022/medicareV2",
            liveUrl: "#",
          },
          {
            title: "E-commerce Platform",
            description:
              "A full-stack e-commerce platform with real-time inventory management, order tracking and payment processing",
            images: [
              "/images/skincareclinic1.png",
              "/images/skincareclinic2.png",
              "/images/skincareclinic3.png",
            ],
            technologies: ["Restframework", "vue", "Django", "Paystack"],
            githubUrl: "https://github.com/kinging1022/skincareclinic",
            liveUrl: "#",
          },
          
        ],
      }
    }
  }
  </script>
  
  <style scoped>
  /* Add any component-specific styles here */
  </style>