<template>
  <div class="min-h-screen flex flex-col bg-base-100 text-base-content antialiased">
    <AppNavbar />
    <main class="flex-1">
      <NuxtPage />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
useSeoMeta({
  title: 'Atividade Prática — Nuxt 4 + Vue.js 3 + Node.js',
  ogTitle: 'Atividade Prática — Nuxt 4 + Vue.js 3 + Node.js',
  description: 'Aplicação construída com Nuxt 4, Vue.js 3 Composition API, DaisyUI e Tailwind CSS.',
  ogDescription: 'Aplicação construída com Nuxt 4, Vue.js 3 Composition API, DaisyUI e Tailwind CSS.',
  ogImage: 'https://nuxt.com/assets/design-kit/logo-text-positive.png',
  twitterCard: 'summary_large_image',
})
</script>
