<template>
  <div class="min-h-[50vh] flex flex-col items-center justify-center text-center p-8">
    <span class="loading loading-spinner loading-lg text-primary"></span>
    <p class="mt-4 text-sm text-base-content/70 font-medium">Redirecionando para o formulário de cadastro...</p>
  </div>
</template>

<script setup>
await navigateTo('/cadastro', { replace: true })
</script>
