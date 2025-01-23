<template>
    <div class="relative w-full overflow-hidden" :style="containerStyle">
      <transition-group name="fade" mode="out-in">
        <div
          v-for="(image, index) in images"
          :key="index"
          class="absolute top-0 left-0 w-full h-full"
          v-show="index === currentIndex"
        >
          <img
            :src="image"
            :alt="`${title} - Image ${index + 1}`"
            class="w-full h-full object-contain"
            @load="onImageLoad(index, $event)"
          />
        </div>
      </transition-group>
      <button
        @click="handlePrevious"
        class="absolute left-2 top-1/2 -translate-y-1/2 bg-black/50 p-2 rounded-full text-white transition-colors hover:bg-black/70"
        aria-label="Previous image"
      >
        <ChevronLeft :size="20" />
      </button>
      <button
        @click="handleNext"
        class="absolute right-2 top-1/2 -translate-y-1/2 bg-black/50 p-2 rounded-full text-white transition-colors hover:bg-black/70"
        aria-label="Next image"
      >
        <ChevronRight :size="20" />
      </button>
      <div class="absolute bottom-2 left-1/2 -translate-x-1/2 flex gap-2">
        <button
          v-for="(_, index) in images"
          :key="index"
          @click="handleDotClick(index)"
          :class="[
            'w-2 h-2 rounded-full transition-colors cursor-pointer hover:bg-blue-400',
            index === currentIndex ? 'bg-blue-500' : 'bg-white/50'
          ]"
          :aria-label="`Go to image ${index + 1}`"
        />
      </div>
    </div>
  </template>
  
  <script>
  import { ChevronLeft, ChevronRight } from 'lucide-vue-next'
  
  export default {
    name: 'ImageCarousel',
    components: {
      ChevronLeft,
      ChevronRight
    },
    props: {
      images: Array,
      title: String
    },
    data() {
      return {
        currentIndex: 0,
        imageAspectRatios: [],
        containerWidth: 0,
        containerHeight: 0
      }
    },
    computed: {
      containerStyle() {
        if (this.imageAspectRatios.length === 0) {
          return { paddingBottom: '56.25%' } // Default 16:9 aspect ratio
        }
        const aspectRatio = this.imageAspectRatios[this.currentIndex] || this.imageAspectRatios[0]
        return {
          paddingBottom: `${(1 / aspectRatio) * 100}%`,
          maxWidth: `${this.containerWidth}px`,
          maxHeight: `${this.containerHeight}px`
        }
      }
    },
    methods: {
      handlePrevious() {
        this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length
      },
      handleNext() {
        this.currentIndex = (this.currentIndex + 1) % this.images.length
      },
      handleDotClick(index) {
        this.currentIndex = index
      },
      onImageLoad(index, event) {
        const img = event.target
        this.imageAspectRatios[index] = img.naturalWidth / img.naturalHeight
        this.$forceUpdate() // Ensure the computed property is recalculated
        
        // Update container dimensions
        if (index === 0) {
          this.containerWidth = img.naturalWidth
          this.containerHeight = img.naturalHeight
        }
      },
      preloadImages() {
        this.images.forEach((src, index) => {
          const img = new Image()
          img.onload = () => this.onImageLoad(index, { target: img })
          img.src = src
        })
      }
    },
    mounted() {
      this.preloadImages()
      window.addEventListener('resize', this.handleResize)
    },
    beforeUnmount() {
      window.removeEventListener('resize', this.handleResize)
    }
  }
  </script>
  
  <style scoped>
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s ease;
  }
  
  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
  </style>