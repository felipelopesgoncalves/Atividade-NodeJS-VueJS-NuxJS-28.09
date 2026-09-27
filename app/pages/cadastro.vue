<template>
  <div class="container mx-auto px-4 py-8 max-w-6xl">
    <!-- Header da Página -->
    <div class="mb-8">
      <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4 border-b border-base-300 pb-5">
        <div>
          <div class="flex items-center gap-2 mb-2">
            <span class="badge badge-primary badge-sm">Atividade Nuxt + Vue</span>
            <span class="text-xs text-base-content/60">Parte B: Formulário Reativo</span>
          </div>
          <h1 class="text-3xl font-extrabold tracking-tight">Cadastro de Novo Membro</h1>
          <p class="text-sm text-base-content/70 mt-1">
            Preencha os campos abaixo. Este formulário demonstra a reatividade do Vue 3 (Composition API), validações e feedback visual.
          </p>
        </div>

        <div class="flex items-center gap-2">
          <NuxtLink to="/" class="btn btn-sm btn-ghost">
            ← Início
          </NuxtLink>
          <NuxtLink to="/example" class="btn btn-sm btn-outline">
            Ver Exemplo
          </NuxtLink>
        </div>
      </div>
    </div>

    <!-- Alerta de Sucesso (Feedback Visual) -->
    <div v-if="submittedSuccess" class="alert alert-success shadow-lg mb-8 transition-all duration-300">
      <svg xmlns="http://www.w3.org/2000/svg" class="stroke-current shrink-0 h-6 w-6" fill="none" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      <div class="flex-1">
        <h3 class="font-bold text-base">Cadastro realizado com sucesso! 🎉</h3>
        <div class="text-xs opacity-90">
          Os dados foram validados e registrados reativamente. Veja o log detalhado no console do navegador (F12).
        </div>
      </div>
      <div class="flex gap-2">
        <button class="btn btn-sm btn-outline btn-neutral" @click="resetForm">
          Cadastrar Outro Membro
        </button>
      </div>
    </div>

    <!-- Layout Grid: Formulário à Esquerda, Live Preview à Direita -->
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
      <!-- Formulário de Cadastro (7 colunas) -->
      <div class="lg:col-span-7">
        <div class="card bg-base-100 border border-base-300 shadow-md">
          <div class="card-body p-6 sm:p-8">
            <h2 class="card-title text-xl font-bold flex items-center gap-2 mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
              </svg>
              Dados do Membro
            </h2>

            <form @submit.prevent="handleSubmit" novalidate class="space-y-5">
              <!-- 1. Nome Completo -->
              <div class="form-control w-full">
                <label class="label py-1" for="nome">
                  <span class="label-text font-semibold flex items-center gap-1">
                    Nome Completo <span class="text-error">*</span>
                  </span>
                  <span v-if="errors.nome" class="label-text-alt text-error font-medium">{{ errors.nome }}</span>
                </label>
                <input
                  id="nome"
                  v-model.trim="form.nome"
                  type="text"
                  placeholder="Ex: Felipe Henrique Silva Junior Pereira Azule"
                  class="input input-bordered w-full"
                  :class="{ 'input-error': errors.nome }"
                  autocomplete="name"
                  required
                  @blur="validateField('nome')"
                />
              </div>

              <!-- 2. E-mail -->
              <div class="form-control w-full">
                <label class="label py-1" for="email">
                  <span class="label-text font-semibold flex items-center gap-1">
                    E-mail Institucional / Pessoal <span class="text-error">*</span>
                  </span>
                  <span v-if="errors.email" class="label-text-alt text-error font-medium">{{ errors.email }}</span>
                </label>
                <input
                  id="email"
                  v-model.trim="form.email"
                  type="email"
                  placeholder="Ex: felipe.h.silva@academico.unirv.edu.br"
                  class="input input-bordered w-full"
                  :class="{ 'input-error': errors.email }"
                  autocomplete="email"
                  required
                  @blur="validateField('email')"
                />
              </div>

              <!-- Linha Dupla: Curso e Semestre -->
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <!-- 3. Curso / Área de Atuação -->
                <div class="form-control w-full">
                  <label class="label py-1" for="curso">
                    <span class="label-text font-semibold flex items-center gap-1">
                      Curso / Área <span class="text-error">*</span>
                    </span>
                    <span v-if="errors.curso" class="label-text-alt text-error font-medium">{{ errors.curso }}</span>
                  </label>
                  <select
                    id="curso"
                    v-model="form.curso"
                    class="select select-bordered w-full"
                    :class="{ 'select-error': errors.curso }"
                    required
                    @change="validateField('curso')"
                  >
                    <option value="" disabled selected>Selecione seu curso...</option>
                    <option value="Ciência da Computação">Ciência da Computação</option>
                    <option value="Engenharia de Software">Engenharia de Software</option>
                    <option value="Sistemas de Informação">Sistemas de Informação</option>
                    <option value="Análise e Desenv. de Sistemas">Análise e Desenv. de Sistemas (ADS)</option>
                    <option value="Engenharia da Computação">Engenharia da Computação</option>
                    <option value="Design Digital / UI-UX">Design Digital / UI-UX</option>
                    <option value="Inteligência Artificial">Inteligência Artificial</option>
                    <option value="Outro">Outra Área de Tecnologia</option>
                  </select>
                </div>

                <!-- 4. Semestre / Período -->
                <div class="form-control w-full">
                  <label class="label py-1" for="semestre">
                    <span class="label-text font-semibold flex items-center gap-1">
                      Semestre / Período <span class="text-error">*</span>
                    </span>
                    <span v-if="errors.semestre" class="label-text-alt text-error font-medium">{{ errors.semestre }}</span>
                  </label>
                  <select
                    id="semestre"
                    v-model="form.semestre"
                    class="select select-bordered w-full"
                    :class="{ 'select-error': errors.semestre }"
                    required
                    @change="validateField('semestre')"
                  >
                    <option value="" disabled selected>Selecione o semestre...</option>
                    <option v-for="n in 10" :key="n" :value="`${n}º Semestre`">
                      {{ n }}º Semestre
                    </option>
                    <option value="Formado / Concluído">Formado / Concluído</option>
                  </select>
                </div>
              </div>

              <!-- 5. Interesses / Habilidades (Checkboxes) -->
              <div class="form-control w-full">
                <label class="label py-1">
                  <span class="label-text font-semibold flex items-center gap-1">
                    Interesses & Habilidades <span class="text-error">*</span>
                  </span>
                  <span v-if="errors.interesses" class="label-text-alt text-error font-medium">{{ errors.interesses }}</span>
                </label>
                <p class="text-xs text-base-content/60 mb-2">Selecione pelo menos uma área de maior interesse:</p>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5 p-3.5 bg-base-200/50 rounded-xl border border-base-300">
                  <label
                    v-for="hab in habilidadesDisponiveis"
                    :key="hab.id"
                    class="label cursor-pointer justify-start gap-3 p-1.5 rounded-lg hover:bg-base-200 transition"
                  >
                    <input
                      v-model="form.interesses"
                      type="checkbox"
                      :value="hab.nome"
                      class="checkbox checkbox-primary checkbox-sm"
                      @change="validateField('interesses')"
                    />
                    <span class="label-text text-sm font-medium flex items-center gap-1.5">
                      <span>{{ hab.icone }}</span>
                      <span>{{ hab.nome }}</span>
                    </span>
                  </label>
                </div>
              </div>

              <!-- 6. Mensagem / Bio Curta -->
              <div class="form-control w-full">
                <div class="label py-1">
                  <label class="label-text font-semibold" for="bio">Mensagem / Bio Curta</label>
                  <span
                    class="label-text-alt text-xs font-mono"
                    :class="{ 'text-error font-bold': form.bio.length >= maxBioLength }"
                  >
                    {{ form.bio.length }} / {{ maxBioLength }} caracteres
                  </span>
                </div>
                <textarea
                  id="bio"
                  v-model="form.bio"
                  :maxlength="maxBioLength"
                  placeholder="Escreva uma breve apresentação sobre seus objetivos, tecnologias de interesse ou experiências..."
                  rows="3"
                  class="textarea textarea-bordered w-full leading-relaxed"
                ></textarea>
                <label class="label py-0.5">
                  <span class="label-text-alt text-xs text-base-content/60">
                    Opcional: compartilhe um resumo do seu perfil.
                  </span>
                </label>
              </div>

              <!-- 7. Botão de Submissão e Ações -->
              <div class="pt-4 border-t border-base-300 flex flex-col sm:flex-row items-center gap-3">
                <button
                  type="submit"
                  class="btn btn-primary w-full sm:w-auto min-w-[160px] shadow-sm"
                  :disabled="isSubmitting"
                >
                  <span v-if="isSubmitting" class="loading loading-spinner loading-sm"></span>
                  <span v-else class="flex items-center gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    Enviar Cadastro
                  </span>
                </button>

                <button
                  type="button"
                  class="btn btn-ghost w-full sm:w-auto text-base-content/70 hover:text-base-content"
                  @click="resetForm"
                >
                  Limpar Campos
                </button>

                <span class="text-xs text-base-content/50 sm:ml-auto">
                  * Campos obrigatórios
                </span>
              </div>
            </form>
          </div>
        </div>
      </div>

      <!-- Live Preview Reativo (5 colunas) -->
      <div class="lg:col-span-5 space-y-6">
        <!-- Card de Prévia em Tempo Real -->
        <div class="card bg-base-100 border border-base-300 shadow-md sticky top-24">
          <div class="card-body p-6">
            <div class="flex items-center justify-between border-b border-base-300 pb-3 mb-4">
              <h3 class="font-bold text-sm uppercase tracking-wider text-base-content/70 flex items-center gap-2">
                <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse"></span>
                Prévia Reativa (v-model)
              </h3>
              <span class="badge badge-neutral badge-xs">Vue 3 Live</span>
            </div>

            <!-- Crachá do Membro -->
            <div class="p-5 bg-gradient-to-br from-base-200/80 to-base-300/40 rounded-2xl border border-base-300 text-center">
              <div class="avatar placeholder mb-3">
                <div class="bg-primary text-primary-content rounded-full w-16 h-16 ring-4 ring-primary/20 shadow-md">
                  <span class="text-2xl font-bold uppercase">{{ avatarInitials }}</span>
                </div>
              </div>

              <h4 class="font-bold text-lg text-base-content leading-snug">
                {{ form.nome || 'Seu Nome Completo' }}
              </h4>
              <p class="text-xs text-base-content/70 mt-0.5">
                {{ form.email || 'seu.email@exemplo.com' }}
              </p>

              <div class="mt-3 flex flex-wrap gap-1.5 justify-center">
                <span class="badge badge-primary badge-sm font-semibold">
                  {{ form.curso || 'Curso não selecionado' }}
                </span>
                <span v-if="form.semestre" class="badge badge-outline badge-sm">
                  {{ form.semestre }}
                </span>
              </div>

              <!-- Habilidades Selecionadas -->
              <div class="mt-4 pt-3 border-t border-base-300/60 text-left">
                <span class="text-xs font-semibold text-base-content/70 block mb-1.5">
                  Interesses Selecionados:
                </span>
                <div v-if="form.interesses.length > 0" class="flex flex-wrap gap-1">
                  <span
                    v-for="interesse in form.interesses"
                    :key="interesse"
                    class="badge badge-accent badge-sm font-medium"
                  >
                    {{ interesse }}
                  </span>
                </div>
                <p v-else class="text-xs text-base-content/40 italic">
                  Nenhum interesse marcado ainda.
                </p>
              </div>

              <!-- Bio Preview -->
              <div class="mt-3 pt-3 border-t border-base-300/60 text-left">
                <span class="text-xs font-semibold text-base-content/70 block mb-1">
                  Bio / Apresentação:
                </span>
                <p class="text-xs text-base-content/80 italic leading-relaxed break-words">
                  {{ form.bio || 'Sua bio aparecerá aqui conforme você digita...' }}
                </p>
              </div>
            </div>

            <!-- Dados Salvos Recentemente -->
            <div v-if="lastSubmitted" class="mt-4 p-4 rounded-xl bg-success/10 border border-success/30 text-xs">
              <div class="font-bold text-success flex items-center gap-1.5 mb-1">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
                Último Cadastro Confirmado:
              </div>
              <p><strong>Nome:</strong> {{ lastSubmitted.nome }}</p>
              <p><strong>E-mail:</strong> {{ lastSubmitted.email }}</p>
              <p><strong>Curso:</strong> {{ lastSubmitted.curso }} ({{ lastSubmitted.semestre }})</p>
              <p><strong>Interesses:</strong> {{ lastSubmitted.interesses.join(', ') }}</p>
              <p class="text-base-content/50 mt-1 text-[11px]">Submetido em {{ lastSubmitted.timestamp }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Metadados de SEO da Página
useSeoMeta({
  title: 'Formulário de Cadastro — Nuxt 4 + Vue 3',
  description: 'Página de formulário de cadastro desenvolvida com Nuxt 4, Vue 3 Composition API e DaisyUI.'
})

// Constantes
const maxBioLength = 200

const habilidadesDisponiveis = [
  { id: 'fe', nome: 'Front-end (Vue.js / Nuxt)', icone: '🎨' },
  { id: 'be', nome: 'Back-end (Node.js / APIs)', icone: '⚙️' },
  { id: 'mob', nome: 'Mobile (Flutter / React Native)', icone: '📱' },
  { id: 'ux', nome: 'UI/UX Design & Prototipagem', icone: '✨' },
  { id: 'ops', nome: 'DevOps, Docker & Cloud', icone: '☁️' },
  { id: 'ai', nome: 'IA & Ciência de Dados', icone: '🤖' }
]

// Estado Reativo do Formulário (Composition API: reactive)
const form = reactive({
  nome: '',
  email: '',
  curso: '',
  semestre: '',
  interesses: [],
  bio: ''
})

// Estado de Erros de Validação
const errors = reactive({
  nome: '',
  email: '',
  curso: '',
  semestre: '',
  interesses: ''
})

// Estados de Controle da Interface (ref)
const isSubmitting = ref(false)
const submittedSuccess = ref(false)
const lastSubmitted = ref(null)

// Iniciais do Avatar calculadas reativamente
const avatarInitials = computed(() => {
  if (!form.nome) return '?'
  const parts = form.nome.trim().split(/\s+/)
  if (parts.length === 1) return parts[0].substring(0, 2)
  return `${parts[0][0]}${parts[parts.length - 1][0]}`
})

// Validação individual por campo
function validateField(field) {
  switch (field) {
    case 'nome':
      if (!form.nome) {
        errors.nome = 'O nome completo é obrigatório.'
      } else if (form.nome.length < 3) {
        errors.nome = 'O nome deve ter no mínimo 3 caracteres.'
      } else {
        errors.nome = ''
      }
      break

    case 'email':
      if (!form.email) {
        errors.email = 'O e-mail é obrigatório.'
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
        errors.email = 'Digite um e-mail válido (ex: usuario@email.com).'
      } else {
        errors.email = ''
      }
      break

    case 'curso':
      if (!form.curso) {
        errors.curso = 'Selecione seu curso ou área de atuação.'
      } else {
        errors.curso = ''
      }
      break

    case 'semestre':
      if (!form.semestre) {
        errors.semestre = 'Selecione o semestre/período.'
      } else {
        errors.semestre = ''
      }
      break

    case 'interesses':
      if (!form.interesses || form.interesses.length === 0) {
        errors.interesses = 'Selecione pelo menos uma área de interesse.'
      } else {
        errors.interesses = ''
      }
      break
  }
}

// Validação Geral de todos os campos
function validateAll() {
  validateField('nome')
  validateField('email')
  validateField('curso')
  validateField('semestre')
  validateField('interesses')

  return !errors.nome && !errors.email && !errors.curso && !errors.semestre && !errors.interesses
}

// Submissão do Formulário
async function handleSubmit() {
  submittedSuccess.value = false

  if (!validateAll()) {
    // Alerta caso existam campos pendentes
    console.warn('⚠️ Validação falhou. Verifique os campos obrigatórios:', errors)
    return
  }

  isSubmitting.value = true

  // Simulação de processamento assíncrono (feedback visual de envio)
  await new Promise(resolve => setTimeout(resolve, 600))

  // Objeto dos dados submetidos
  const submissionData = {
    nome: form.nome,
    email: form.email,
    curso: form.curso,
    semestre: form.semestre,
    interesses: [...form.interesses],
    bio: form.bio || '(Nenhuma bio informada)',
    timestamp: new Date().toLocaleTimeString('pt-BR')
  }

  lastSubmitted.value = submissionData
  submittedSuccess.value = true
  isSubmitting.value = false

  // Feedback no Console conforme requisitos da atividade
  console.log(
    '%c🎉 NOVO MEMBRO CADASTRADO COM SUCESSO!',
    'background: #10b981; color: white; font-weight: bold; font-size: 14px; padding: 6px 12px; border-radius: 6px;'
  )
  console.log('%cDados Reativos Enviados (Vue 3 Composition API):', 'color: #065f46; font-weight: bold;')
  console.table(submissionData)

  // Scroll suave para o topo para visualizar o feedback de sucesso
  if (typeof window !== 'undefined') {
    window.scrollTo({ top: 0, behavior: 'smooth' })
  }
}

// Limpeza reativa dos campos
function resetForm() {
  form.nome = ''
  form.email = ''
  form.curso = ''
  form.semestre = ''
  form.interesses = []
  form.bio = ''

  errors.nome = ''
  errors.email = ''
  errors.curso = ''
  errors.semestre = ''
  errors.interesses = ''

  submittedSuccess.value = false
  console.log('🔄 Formulário limpo e resetado reativamente.')
}
</script>
