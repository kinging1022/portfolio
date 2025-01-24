<template>
  <div class="min-h-screen bg-gray-900 text-white">
    <main class="container mx-auto px-6 py-12">
      <!-- Home Section -->
      <div class="flex flex-col md:flex-row items-center gap-12 mb-16">
        <div class="w-full md:w-1/2 flex justify-center">
          <div class="w-64 h-64 rounded-full overflow-hidden">
            <img
              src="/images/headshot.jpeg"
              alt="Profile avatar"
              class="w-full h-full object-cover"
            />
          </div>
        </div>
        <div class="w-full md:w-1/2 text-center md:text-left">
          <p class="text-xl mb-2">
            <span class="text-white">Hi, </span>
            <span class="text-white">I am </span>
            <span class="text-blue-500">Backend Developer</span>
          </p>
          <h1 class="text-4xl font-bold text-blue-500 mb-4">Emmanuel Igho</h1>
          <p class="text-gray-200 mb-8 leading-relaxed">
            Passionate backend developer with expertise in building scalable
            and efficient server-side applications. Specialized in creating
            robust APIs and implementing complex business logic.
          </p>
          <div class="flex gap-4 justify-center md:justify-start">
            <a
              href="/pdf/cv.pdf"
              download
              class="px-6 py-2 border border-blue-500 text-white rounded-full hover:bg-blue-500/10 transition-colors flex items-center gap-2"
            >
              <DownloadIcon :size="20" />
              Download CV
            </a>
            <button 
              @click="toggleProjects" 
              class="px-6 py-2 border border-white text-white rounded-full hover:bg-white/10 transition-colors"
            >
              Projects
            </button>
          </div>
          <div class="flex gap-6 mt-8 justify-center md:justify-start">
            <a
              href="mailto:emmanuelemmy0906@gmail.com"
              class="text-white hover:text-blue-500 transition-colors"
              aria-label="Email"
            >
              <MailIcon :size="24" />
            </a>
            <a
              href="https://www.linkedin.com/in/emmanuel-igho-292708264/"
              class="text-white hover:text-blue-500 transition-colors"
              aria-label="LinkedIn"
            >
              <LinkedinIcon :size="24" />
            </a>
            <a
              href="https://github.com/kinging1022?tab=repositories"
              class="text-white hover:text-blue-500 transition-colors"
              aria-label="GitHub"
            >
              <GithubIcon :size="24" />
            </a>
          </div>
        </div>
      </div>

      <!-- Projects Section -->
      <div v-if="showProjects" class="mt-16">
        <div class="mb-12">
          <h2 class="text-4xl font-bold text-white mb-4">My Projects</h2>
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
      </div>
    </main>
  </div>
</template>

<script>
import { DownloadIcon, MailIcon, LinkedinIcon, GithubIcon } from 'lucide-vue-next'
import ProjectCard from '@/assets/components/ProjectCard.vue';

export default {
  name: 'App',
  components: {
    ProjectCard,
    DownloadIcon,
    MailIcon,
    LinkedinIcon,
    GithubIcon
  },
  data() {
    return {
      showProjects: false,
      projects: [
        {
          title: "Playlist Pilot",
          description: "PlaylistPilot is an innovative AI-powered app designed to automatically create personalized Spotify playlists. It offers two unique features: the Time Machine, which lets users revisit Billboard Hot 100 hits from any date, and the AI-curated playlists, which provide a custom playlist tailored to the user's preferences. Both features effortlessly generate playlists, providing a seamless, personalized music experience.",
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
          description: "A full-stack e-commerce platform with real-time inventory management, order tracking and payment processing",
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
  },
  methods: {
    toggleProjects() {
      this.showProjects = !this.showProjects
    }
  }
}
</script>

<style scoped>
/* Add any component-specific styles here */
</style>