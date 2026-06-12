# FRONTEND.md
# PROFEPLAN V4
## Frontend Architecture (A Loja)

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O frontend da V4.0 (conhecido na arquitetura "Holding Industrial" como "A Loja") é projetado para ser uma interface extremamente rápida, fluida e focada no professor.

Seu principal papel é capturar as intenções do usuário (parâmetros de turmas, seleções de habilidades, comandos de voz) e exibir os resultados processados de maneira limpa.

---

# 2. STACK TECNOLÓGICO

* **Framework Core:** React 18
* **Linguagem:** TypeScript
* **Build tool:** Vite
* **Estilização:** TailwindCSS v4
* **Roteamento:** React Router v6
* **Mobile Wrap:** Capacitor (para envelopamento nativo Android)

---

# 3. FILOSOFIA DE DESENVOLVIMENTO

## Leveza e Agilidade
O frontend não realiza operações pesadas de processamento de dados (parsing de arquivos, ordenamento matemático complexo, computação de embeddings). Ele delega tudo para "As Indústrias" (backend Python) e bancos de dados Supabase.

---

## State Management
* Estados locais e simples são mantidos no contexto nativo do React (`Context API` e `useState`).
* Integração direta com a API do Supabase Client para controle de autenticação e escutas em tempo real.

---

# 4. COMPORTAMENTOS ESPECIAIS

## Modal de Configurações Mandatório
Interseptador de rota que verifica se o perfil profissional do usuário está cadastrado. Em caso negativo, bloqueia a UI e força a abertura do onboarding.

---

## Editor Modo Foco
Editor enriquecido que oculta todos os painéis e barras laterais da interface web, deixando o professor com uma visualização de "folha de papel" limpa para edição final do planejamento ou avaliação.

---

## Painel Flutuante FREEDAY
Componente React global inserido no layout raiz da aplicação para permitir que o assistente de voz esteja disponível em qualquer tela do sistema.
