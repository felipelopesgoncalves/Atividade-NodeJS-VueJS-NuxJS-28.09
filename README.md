# Atividade Prática: Ecossistema Moderno (Node.js + Vue.js + Nuxt 4)

Este projeto foi desenvolvido como parte da atividade prática para consolidar o aprendizado sobre o ecossistema moderno de desenvolvimento web com **Node.js**, **Vue.js 3** e **Nuxt 4**.

---

## 🎯 Objetivos Implementados

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

## 🚀 Como Executar o Projeto (Guia de Clone e Execução)

### Pré-requisitos
- **Node.js** instalado (versão 20 LTS recomendada ou superior)
- **Git** instalado

### Passo a Passo para quem clonar o repositório

1. **Clone o repositório**:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   ```

2. **Acesse a pasta do projeto**:
   ```bash
   cd <NOME_DA_PASTA_DO_REPOSITORIO>
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

## 🧭 Rotas da Aplicação

| Rota | Descrição |
| :--- | :--- |
| `/` | Página inicial com apresentação, métricas e botões de navegação rápida |
| `/example` | Página com o componente `WindowLP` reproduzido da aula de Nuxt |
| `/cadastro` | Formulário completo de cadastro de membros com validações e preview reativo |
| `/novo-membro` | Rota alternativa que redireciona automaticamente para `/cadastro` |

---

## 🎥 Roteiro para o Vídeo de Demonstração (2 a 3 minutos)

1. **Página Inicial (`/`)**:
   - Mostre a aplicação rodando no navegador a partir de `http://localhost:3000`.
   - Destaque o layout responsivo e a barra de navegação superior (`AppNavbar`).
2. **Navegação SPA**:
   - Clique em "Exemplo da Aula" na navbar ou no botão da página inicial para exibir a rota `/example`.
   - Em seguida, clique em "Cadastro de Membro" ou no botão "Novo Membro", demonstrando a navegação fluida sem recarregar a página.
3. **Formulário Reativo (`/cadastro`)**:
   - Abra o Console do navegador (pressione `F12` e vá para a aba **Console**).
   - Tente submeter o formulário vazio para mostrar as **mensagens de validação** em vermelho nos campos obrigatórios.
   - Comece a preencher: à medida que você digita o nome, o curso e marca as habilidades, aponte para o **Card de Prévia à direita**, mostrando a reatividade do `v-model` e avatar atualizando em tempo real.
   - Digite uma bio para demonstrar o contador de caracteres se atualizando dinamicamente.
4. **Submissão e Feedback Visual**:
   - Clique em **Enviar Cadastro**.
   - Mostre o **Alerta de Sucesso** verde na tela e a tabela de dados impressa no **Console do Navegador**.
   - Demonstre o botão **Limpar Campos** ou **Cadastrar Outro Membro** resetando o formulário reativamente.