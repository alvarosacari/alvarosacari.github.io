<script setup lang="ts">
interface NavItem {
  label: string
  href: string
}

interface Props {
  logo: string
  navItems: NavItem[]
}

const props = defineProps<Props>()

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<template>
  <header class="fixed top-0 left-0 right-0 z-50 bg-gray-900/90 backdrop-blur-md border-b border-gray-800">
    <nav class="max-w-6xl mx-auto px-6 py-5 flex justify-between items-center">
      <!-- Logo -->
      <a href="#" class="text-2xl font-bold text-white tracking-tight">
        {{ logo }}
      </a>

      <!-- Desktop Navigation -->
      <div class="hidden md:flex items-center gap-10">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="text-sm text-gray-400 hover:text-white transition tracking-wide uppercase"
        >
          {{ item.label }}
        </a>
      </div>

      <!-- Mobile Menu Button -->
      <button
        class="md:hidden p-2 text-gray-400 hover:text-white transition"
        @click="toggleMenu"
        aria-label="Toggle menu"
      >
        <svg
          v-if="!isMenuOpen"
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg
          v-else
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </nav>

    <!-- Mobile Navigation -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div
        v-if="isMenuOpen"
        class="md:hidden border-t border-gray-800 bg-gray-900/95 backdrop-blur-md"
      >
        <div class="px-6 py-4 space-y-3">
          <a
            v-for="item in navItems"
            :key="item.href"
            :href="item.href"
            class="block py-2 text-gray-400 hover:text-white transition"
            @click="closeMenu"
          >
            {{ item.label }}
          </a>
        </div>
      </div>
    </Transition>
  </header>
</template>