<template>
  <div class="hero bg-base-200 min-h-[calc(100vh-64px)]">
    <div class="hero-content text-center py-12">
      <div class="max-w-xl">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/10 text-emerald-600 text-xs font-semibold mb-4 border border-emerald-500/20">
          <span>Ecossistema Moderno</span>
          <span>•</span>
          <span>Node.js, Vue 3 & Nuxt 4</span>
        </div>

        <h1 class="text-4xl sm:text-5xl font-extrabold tracking-tight">
          Olá Mundo! 👋
        </h1>

        <p class="py-6 text-base text-base-content/80 max-w-lg mx-auto leading-relaxed">
          Esta aplicação reproduz o projeto prático desenvolvido com <strong>Nuxt 4</strong> e <strong>DaisyUI</strong>, 
          estendendo-a com uma nova funcionalidade completa: uma página com formulário de cadastro reativo com validação e feedback visual.
        </p>

        <div class="flex flex-col sm:flex-row gap-3 justify-center items-center">
          <button class="btn btn-primary shadow-md w-full sm:w-auto" @click="goToCadastro()">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z" />
            </svg>
            Ir para Formulário de Cadastro
          </button>

          <button class="btn btn-outline w-full sm:w-auto" @click="goToExample()">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
            Ver Exemplo da Aula
          </button>
        </div>

        <div class="mt-10 grid grid-cols-3 gap-3 max-w-md mx-auto pt-6 border-t border-base-300 text-xs text-base-content/70">
          <div class="flex flex-col items-center">
            <span class="font-bold text-base text-base-content">100%</span>
            <span>Performance SSR</span>
          </div>
          <div class="flex flex-col items-center">
            <span class="font-bold text-base text-base-content">Vue 3</span>
            <span>Composition API</span>
          </div>
          <div class="flex flex-col items-center">
            <span class="font-bold text-base text-base-content">Nuxt 4</span>
            <span>File Routing</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const router = useRouter()

function goToExample () {
  router.push('/example')
}

function goToCadastro () {
  router.push('/cadastro')
}
</script>