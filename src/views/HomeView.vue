<template>
  <div>
    <main class="container mx-auto px-6 py-12">
      <div class="flex flex-col md:flex-row items-center gap-12">
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
            <RouterLink to="/projects" class="px-6 py-2 border border-white text-white rounded-full hover:bg-white/10 transition-colors">
              Projects
            </RouterLink>
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
    </main>
  </div>
</template>

<script>
import { DownloadIcon, MailIcon, LinkedinIcon, GithubIcon } from 'lucide-vue-next'

export default {
  name: 'App',
  components: {
    DownloadIcon,
    MailIcon,
    LinkedinIcon,
    GithubIcon
  }
}
</script>

<style scoped>
/* Add any component-specific styles here */
</style>
