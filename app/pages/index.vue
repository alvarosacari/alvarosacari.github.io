<script setup lang="ts">
// Developer data - easy to customize
const developer: {
  name: string
  title: string
  location: string
  github: string
  linkedin: string
  email: string
} = {
  name: 'Alvaro Sacari',
  title: 'Frontend Developer',
  location: 'Lima, Peru',
  github: 'https://github.com/alvarosacari',
  linkedin: 'https://www.linkedin.com/in/alvaro-sacari/',
  email: 'alvarosacari@gmail.com'
}

// Header config
const headerLogo: string = developer.name.split(' ')[0] || ''
const headerNavItems: { label: string; href: string }[] = [
  { label: 'Proyectos', href: '#projects' },
  { label: 'Sobre mí', href: '#about' },
  { label: 'Contacto', href: '#contact' }
]

// Featured projects
const projects = [
  {
    name: 'E-commerce Dashboard',
    description: 'Admin panel with Vue 3, Pinia and Tailwind. Real-time charts and inventory management.',
    techs: ['Vue 3', 'Pinia', 'Tailwind', 'Chart.js'],
    demo: '#',
    repo: '#'
  },
  {
    name: 'Task Manager App',
    description: 'Productivity app with project management, kanban and real-time collaboration.',
    techs: ['React', 'TypeScript', 'Zustand', 'Firebase'],
    demo: '#',
    repo: '#'
  },
  {
    name: 'Weather API Client',
    description: 'Weather client with geolocation, 7-day forecast and offline mode.',
    techs: ['Next.js', 'TypeScript', 'PWA', 'OpenWeather'],
    demo: '#',
    repo: '#'
  }
]

// Tech stack
const techs = [
  { name: 'Vue.js', icon: '💚' },
  { name: 'React', icon: '⚛️' },
  { name: 'TypeScript', icon: '🔷' },
  { name: 'Tailwind', icon: '🎨' },
  { name: 'Pinia', icon: '📦' },
  { name: 'Next.js', icon: '▲' },
  { name: 'Node.js', icon: '🟢' },
  { name: 'Git', icon: '📂' }
]
</script>

<template>
  <div class="min-h-screen bg-gray-900 text-white font-sans">
    <!-- Header Component -->
    <AppHeader :logo="headerLogo" :nav-items="headerNavItems" />

    <!-- Hero Section -->
    <section class="min-h-screen flex items-center justify-center px-6 pt-24">
      <div class="max-w-4xl mx-auto text-center">
        <div class="mb-6 inline-flex items-center gap-2 px-4 py-2 rounded-full bg-emerald-500/10 text-emerald-400 text-sm">
          <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
          Disponible para trabajar
        </div>
        <h1 class="text-5xl md:text-7xl font-bold mb-6 leading-tight">
          Hola, soy <span class="text-emerald-400">{{ developer.name }}</span>
        </h1>
        <p class="text-xl md:text-2xl text-gray-400 mb-8 max-w-2xl mx-auto">
          {{ developer.title }} creando experiencias web modernas, rápidas y accesibles.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a
            href="#contact"
            class="px-8 py-4 rounded-lg bg-emerald-500 hover:bg-emerald-600 text-gray-900 font-semibold transition transform hover:scale-105"
          >
            ¡Hablemos!
          </a>
          <a
            href="#projects"
            class="px-8 py-4 rounded-lg border border-gray-700 hover:border-emerald-500 text-gray-300 hover:text-emerald-400 font-semibold transition"
          >
            Ver proyectos
          </a>
        </div>
        <div class="mt-12 flex items-center justify-center gap-6 text-gray-500">
          <span class="flex items-center gap-2">📍 {{ developer.location }}</span>
        </div>
      </div>
    </section>

    <!-- Tech Stack -->
    <section class="py-20 px-6 bg-gray-800/50">
      <div class="max-w-6xl mx-auto">
        <h2 class="text-center text-sm uppercase tracking-widest text-gray-500 mb-12">Tech Stack</h2>
        <div class="flex flex-wrap justify-center gap-4">
          <div
            v-for="tech in techs"
            :key="tech.name"
            class="px-4 py-2 rounded-lg bg-gray-800 border border-gray-700 flex items-center gap-2 hover:border-emerald-500 transition"
          >
            <span>{{ tech.icon }}</span>
            <span class="text-gray-300">{{ tech.name }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-20 px-6">
      <div class="max-w-6xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">Proyectos Destacados</h2>
        <p class="text-gray-400 mb-12">Proyectos donde combino funcionalidad con buena UX</p>

        <div class="grid md:grid-cols-3 gap-6">
          <article
            v-for="project in projects"
            :key="project.name"
            class="bg-gray-800 rounded-xl p-6 border border-gray-700 hover:border-emerald-500 transition group"
          >
            <h3 class="text-xl font-semibold mb-2 group-hover:text-emerald-400 transition">
              {{ project.name }}
            </h3>
            <p class="text-gray-400 text-sm mb-4">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2 mb-4">
              <span
                v-for="t in project.techs"
                :key="t"
                class="text-xs px-2 py-1 rounded bg-gray-700 text-gray-300"
              >
                {{ t }}
              </span>
            </div>
            <div class="flex gap-4">
              <a :href="project.demo" class="text-emerald-400 hover:text-emerald-300 text-sm flex items-center gap-1">
                <span>Live</span>
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
                </svg>
              </a>
              <a :href="project.repo" class="text-gray-400 hover:text-white text-sm flex items-center gap-1">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z" />
                </svg>
                <span>Code</span>
              </a>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-20 px-6 bg-gray-800/50">
      <div class="max-w-3xl mx-auto">
        <h2 class="text-3xl md:text-4xl font-bold mb-8">Sobre mí</h2>
        <div class="space-y-4 text-gray-300 leading-relaxed">
          <p>
            Soy desarrollador frontend con +3 años de experiencia creando interfaces modernas y performantes.
            Me especializo en Vue.js y React, aunque siempre estoy explorando nuevas tecnologías.
          </p>
          <p>
            Creo que un buen desarrollo frontend va más allá de hacer que las cosas funcionen —
            se trata de crear experiencias que los usuarios disfruten usar. Cada detalle cuenta,
            desde las microinteracciones hasta el rendimiento.
          </p>
          <p>
            Cuando no estoy codeando, probablemente estoy explorando cómo funcionan las cosas en el mundo del
            UI/UX, o contribuyendo a proyectos open source.
          </p>
        </div>
        <div class="mt-8 pt-8 border-t border-gray-700">
          <h3 class="text-lg font-semibold mb-4">Lo que me define</h3>
          <div class="grid sm:grid-cols-2 gap-4">
            <div class="flex items-center gap-3 text-gray-300">
              <span class="text-emerald-400">✓</span>
              Enfoque en accesibilidad
            </div>
            <div class="flex items-center gap-3 text-gray-300">
              <span class="text-emerald-400">✓</span>
              Performance primero
            </div>
            <div class="flex items-center gap-3 text-gray-300">
              <span class="text-emerald-400">✓</span>
              Mindset UX/UI
            </div>
            <div class="flex items-center gap-3 text-gray-300">
              <span class="text-emerald-400">✓</span>
              Código mantenible
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 px-6">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">¿Trabajamos juntos?</h2>
        <p class="text-gray-400 mb-8">
          Estoy disponible para proyectos freelance, tiempo completo o colaboraciones.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a
            :href="`mailto:${developer.email}`"
            class="px-8 py-4 rounded-lg bg-emerald-500 hover:bg-emerald-600 text-gray-900 font-semibold transition"
          >
            Enviar email
          </a>
          <a
            :href="developer.github"
            target="_blank"
            class="px-8 py-4 rounded-lg border border-gray-700 hover:border-white text-gray-300 hover:text-white font-semibold transition flex items-center justify-center gap-2"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z" />
            </svg>
            GitHub
          </a>
          <a
            :href="developer.linkedin"
            target="_blank"
            class="px-8 py-4 rounded-lg border border-gray-700 hover:border-white text-gray-300 hover:text-white font-semibold transition flex items-center justify-center gap-2"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z" />
            </svg>
            LinkedIn
          </a>
        </div>
      </div>
    </section>

    <!-- Footer Component -->
    <AppFooter
      :name="developer.name"
      :github="developer.github"
      :linkedin="developer.linkedin"
    />
  </div>
</template>
