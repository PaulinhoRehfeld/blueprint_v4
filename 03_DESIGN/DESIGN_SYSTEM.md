# DESIGN_SYSTEM.md
# PROFEPLAN V4
## Design System Principles

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O sistema de design do PROFEPLAN V4 é projetado para oferecer uma experiência de leitura limpa e de baixo cansaço visual, considerando que professores passam horas planejando aulas e corrigindo trabalhos na plataforma.

A estilização utiliza classes utilitárias do TailwindCSS de forma semântica.

---

# 2. COMPONENTES PADRONIZADOS

## Cards de Turma
Componentes visuais retangulares com bordas arredondadas e sombras suaves (`shadow-sm`) que mostram o nome da escola, série, número de alunos e indicadores rápidos como "PDIs Pendentes" com cores de alerta específicas.

---

## Modais e Diálogos
Janelas sobrepostas centralizadas com fundo semi-transparente escurecido. Utilizados no Onboarding obrigatório e na criação rápida de simulados.

---

## Editor em Tela Cheia (Modo Foco)
Interface de layout responsivo que expande a área de texto ao máximo, ocultando navegações e barras laterais para dar a sensação física de edição em folha A4 de papel.

---

# 3. INTERAÇÕES E ANIMAÇÕES

* **Hover states:** Efeitos suaves de transição (`transition-all duration-200`) em botões e cards de turma ao passar o mouse.
* **Micro-animações:** Indicador de loading sutil (pulsante) durante a geração de planos e avaliações pela inteligência artificial.
* **Flutuante Freeday:** Botão circular fixado no canto inferior direito com animação de onda sonora pulsante quando o assistente de voz está ouvindo.
