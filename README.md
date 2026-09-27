# Atividade Prática Node.js + Vue.js + Nuxt 4

Este projeto foi desenvolvido como parte da atividade prática para consolidar o aprendizado sobre o ecossistema moderno de desenvolvimento web com **Node.js**, **Vue.js 3** e **Nuxt 4**.

---

## Objetivos Implementados

### 1. Parte A: Fidelidade ao Projeto Base
- Reprodução completa da aplicação Nuxt demonstrada na aula prática de referência.
- Estruturação moderna com diretório `app/` (Nuxt 4), SSR habilitado, estilização com Tailwind CSS e componentes DaisyUI (`HeroLP.vue` e `WindowLP.vue`).

### 2. Parte B: Nova Rota e Formulário de Cadastro Reativo
Nova página acessível em `/cadastro` (e com alias `/novo-membro`) contendo:
- **Nome Completo**: validação de campo obrigatório e tamanho mínimo (3 caracteres).
- **E-mail**: validação de formato de e-mail e campo obrigatório.
- **Curso / Área de Atuação**: dropdown seletor estilizado.
- **Semestre / Período**: dropdown seletor com períodos letivos (1º ao 10º).
- **Interesses / Habilidades**: múltipla escolha com checkboxes estilizados (Front-end, Back-end, Mobile, UI/UX, DevOps, IA).
- **Mensagem / Bio curta**: textarea com contador reativo de caracteres em tempo real.
- **Botão de Submissão com Feedback Visual**:
  - Alerta de sucesso dinâmico na tela (`alert alert-success`).
  - Log formatado e colorido no console (`console.log` e `console.table`).
  - Limpeza e reset reativo dos campos (`resetForm`).
- **Live Preview Reativo**: card lateral em tempo real que reflete instantaneamente os dados digitados via `v-model` e Composition API (`ref`, `reactive`, `computed`).
- **Barra de Navegação Global (`AppNavbar.vue`)**: navegação SPA suave entre Início, Exemplo da Aula e Cadastro.

---

## Como Executar o Projeto (Guia de Clone e Execução)

### Pré-requisitos
- **Node.js** instalado (versão 20 LTS recomendada ou superior)
- **Git** instalado

### Passo a Passo para quem clonar o repositório

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/felipelopesgoncalves/Atividade-NodeJS-VueJS-NuxJS-28.09.git
   ```

2. **Acesse a pasta do projeto**:
   ```bash
   cd Atividade-NodeJS-VueJS-NuxJS-28.09
   ```

3. **Instale as dependências**:
   ```bash
   npm install
   ```

4. **Inicie o servidor de desenvolvimento**:
   ```bash
   npm run dev
   ```

5. **Acesse no navegador**:
   ```
   http://localhost:3000
   ```

---

## Rotas da Aplicação

| Rota | Descrição |
| :--- | :--- |
| `/` | Página inicial com apresentação, métricas e botões de navegação rápida |
| `/example` | Página com o componente `WindowLP` reproduzido da aula de Nuxt |
| `/cadastro` | Formulário completo de cadastro de membros com validações e preview reativo |
| `/novo-membro` | Rota alternativa que redireciona automaticamente para `/cadastro` |

---
