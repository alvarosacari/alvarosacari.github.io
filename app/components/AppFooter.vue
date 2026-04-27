<script setup lang="ts">
interface Props {
  name: string
  github: string
  linkedin: string
}

defineProps<Props>()

const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="py-8 px-6 border-t border-gray-800">
    <div class="max-w-6xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4 text-gray-500 text-sm">
      <p>
        © {{ currentYear }} {{ name }}. Hecho con ☕ y Vue.js
      </p>
      <div class="flex gap-6">
        <a
          :href="github"
          target="_blank"
          rel="noopener noreferrer"
          class="hover:text-emerald-400 transition"
        >
          GitHub
        </a>
        <a
          :href="linkedin"
          target="_blank"
          rel="noopener noreferrer"
          class="hover:text-emerald-400 transition"
        >
          LinkedIn
        </a>
      </div>
    </div>
  </footer>
</template>