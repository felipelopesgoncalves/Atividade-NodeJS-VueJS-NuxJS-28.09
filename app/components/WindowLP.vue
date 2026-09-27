<template>
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <div class="mb-6 flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-bold">Exemplo da Aula de Nuxt</h1>
        <p class="text-sm text-base-content/70">Página de demonstração do componente WindowLP exibido no vídeo de referência.</p>
      </div>
      <div class="flex gap-2">
        <NuxtLink to="/" class="btn btn-sm btn-ghost">
          ← Voltar ao Início
        </NuxtLink>
        <NuxtLink to="/cadastro" class="btn btn-sm btn-primary">
          Ir para Formulário →
        </NuxtLink>
      </div>
    </div>

    <div class="mockup-window bg-base-200 border border-base-300 shadow-xl">
      <div class="bg-base-100 p-8 flex flex-col items-center justify-center min-h-[350px] text-center gap-4">
        <div class="w-16 h-16 rounded-2xl bg-primary/10 text-primary flex items-center justify-center text-3xl font-black">
          ⚡
        </div>
        <h2 class="text-xl font-bold">Exemplo da nossa aplicação Nuxt</h2>
        <p class="max-w-md text-base-content/70 text-sm">
          Este componente reproduz com precisão o componente <code class="badge badge-neutral">WindowLP.vue</code> da aula de Nuxt, demonstrando o roteamento SPA nativo e componentização Vue 3.
        </p>

        <div class="card bg-base-200/60 p-4 rounded-xl border border-base-300 text-left text-xs max-w-md w-full">
          <div class="font-bold text-sm mb-2 text-base-content">Tecnologias Utilizadas no Exemplo:</div>
          <ul class="list-disc list-inside space-y-1 text-base-content/80">
            <li><strong>Nuxt 4</strong> com renderização SSR e auto-imports</li>
            <li><strong>Vue 3</strong> com Composition API (`&lt;script setup&gt;`)</li>
            <li><strong>Tailwind CSS 4</strong> + <strong>DaisyUI 5</strong> para estilização moderna</li>
            <li><strong>Vue Router 4</strong> para navegação client-side rápida</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>