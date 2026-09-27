<template>
  <header class="navbar bg-base-100/90 backdrop-blur-md sticky top-0 z-50 border-b border-base-200 px-4 lg:px-8">
    <div class="navbar-start">
      <!-- Mobile dropdown -->
      <div class="dropdown">
        <label tabindex="0" class="btn btn-ghost lg:hidden mr-1" aria-label="Abrir menu">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" />
          </svg>
        </label>
        <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow-lg bg-base-100 rounded-box w-52 border border-base-200">
          <li>
            <NuxtLink to="/" active-class="active" class="font-medium">
              Início
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/example" active-class="active" class="font-medium">
              Exemplo (Video)
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/cadastro" active-class="active" class="font-medium">
              Cadastro de Membro
            </NuxtLink>
          </li>
        </ul>
      </div>

      <!-- Brand / Logo -->
      <NuxtLink to="/" class="flex items-center gap-2 text-xl font-bold tracking-tight hover:opacity-90 transition">
        <span class="w-8 h-8 rounded-lg bg-emerald-500 text-white flex items-center justify-center font-black text-base shadow-sm">
          N
        </span>
        <span class="bg-gradient-to-r from-emerald-600 to-teal-500 bg-clip-text text-transparent">
          Nuxt 4 + Vue.js
        </span>
        <span class="badge badge-sm badge-outline hidden sm:inline-flex">Node.js Stack</span>
      </NuxtLink>
    </div>

    <!-- Desktop menu -->
    <div class="navbar-center hidden lg:flex">
      <ul class="menu menu-horizontal px-1 gap-1 text-sm font-medium">
        <li>
          <NuxtLink to="/" active-class="active" class="rounded-lg">
            Início
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="/example" active-class="active" class="rounded-lg">
            Exemplo da Aula
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="/cadastro" active-class="active" class="rounded-lg">
            Formulário de Cadastro
          </NuxtLink>
        </li>
      </ul>
    </div>

    <!-- Right action button -->
    <div class="navbar-end gap-2">
      <NuxtLink to="/cadastro" class="btn btn-primary btn-sm rounded-lg shadow-sm">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18 9v3m0 0v3m0-3h3m-3 0h-3m-2-5a4 4 0 11-8 0 4 4 0 018 0zM3 20a6 6 0 0112 0v1H3v-1z" />
        </svg>
        <span>Novo Membro</span>
      </NuxtLink>
    </div>
  </header>
</template>
