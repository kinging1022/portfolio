<template>
  <div class="w-full min-h-screen bg-gray-900">
    <header class="w-full p-6">

        <RouterLink to="/">
          <div class="flex items-center gap-3">
            <div class="w-12 h-12 rounded-full border-2 border-blue-500 flex items-center justify-center">
              <span class="text-white font-bold text-xl">EI</span>
            </div>
            <span class="text-white font-bold text-xl">Emmanuel Igho</span>
          </div>
        </RouterLink>
      
    </header>

    <RouterView />

   
  </div>
</template>

<script>
import { DownloadIcon, MailIcon, LinkedinIcon, GithubIcon } from 'lucide-vue-next'
import { RouterView, RouterLink } from 'vue-router'

export default {
  name: 'App',
  components: {
    DownloadIcon,
    MailIcon,
    LinkedinIcon,
    GithubIcon,
    
  }
}
</script>

<style scoped>
/* Add any component-specific styles here */
</style>