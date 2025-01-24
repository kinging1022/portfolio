<template>
  <div class="bg-gray-800 rounded-xl overflow-hidden hover:transform hover:scale-[1.02] transition-all duration-300">
    <div class="w-full">
      <ImageCarousel :images="images" :title="title" />
    </div>
    <div class="p-6">
      <h3 class="text-2xl font-bold text-white mb-2">{{ title }}</h3>
      <p class="text-gray-300 mb-4">{{ description }}</p>
      <div class="flex flex-wrap gap-2 mb-4">
        <span
          v-for="tech in technologies"
          :key="tech"
          class="px-3 py-1 bg-blue-500/10 text-blue-400 rounded-full text-sm"
        >
          {{ tech }}
        </span>
      </div>
      <div class="flex gap-4 items-center">
        <a
          v-if="githubUrl"
          :href="githubUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="text-white hover:text-blue-500 transition-colors"
          aria-label="View source on GitHub"
        >
          <Github :size="24" />
        </a>
        <a
          v-if="liveUrl"
          :href="liveUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-1 px-3 py-1 bg-blue-500 text-white rounded-full hover:bg-blue-600 transition-colors"
        >
          <span>Demo</span>
          <ExternalLink :size="16" />
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import { ExternalLink, Github } from 'lucide-vue-next'
import ImageCarousel from './ImageCarousel.vue'

export default {
  name: 'ProjectCard',
  components: {
    ImageCarousel,
    ExternalLink,
    Github
  },
  props: {
    title: String,
    description: String,
    images: Array,
    technologies: Array,
    githubUrl: String,
    liveUrl: String
  }
}
</script>

<style scoped>
.bg-gray-800:hover {
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}
</style>

