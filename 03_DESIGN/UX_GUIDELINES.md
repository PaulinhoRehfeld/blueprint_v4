# UX_GUIDELINES.md
# PROFEPLAN V4
## User Experience Guidelines

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. FOCO NO PROFESSOR

Os fluxos do PROFEPLAN V4 priorizam o imediatismo. O professor deve ser capaz de concluir tarefas comuns com a menor quantidade de cliques possível.

---

# 2. DIRETRIZES DE FLUXOS CRÍTICOS

## 2.1 Fluxo de Onboarding Inicial
* **Ação:** Bloqueio de funcionalidades caso o perfil pedagógico esteja incompleto.
* **UX Rule:** O formulário deve ser simples e preenchido em menos de 2 minutos, permitindo que o professor veja valor imediato na plataforma após o salvamento.

---

## 2.2 Fluxo de Importação Nominal
* **Ação:** Arrastar e soltar o PDF do SIMADE.
* **UX Rule:** O parser deve processar o documento em background e exibir um resumo dos alunos extraídos para validação do professor antes de persistir no banco, evitando cadastros incorretos de turmas.

---

## 2.3 Editor Modo Foco
* **Ação:** Escrita e revisão de planejamentos.
* **UX Rule:** Ao clicar em editar, remova ruídos visuais. Menus suspensos, painéis laterais de navegação e rodapés gerais são minimizados. O foco total do professor deve estar no plano de aula na folha de edição simulada.

---

## 2.4 Interface do Assistente FREEDAY
* **Ação:** Operação por voz.
* **UX Rule:** Dar feedback visual de atividade sempre que o áudio estiver sendo capturado (transcrição parcial do texto em tempo real) e reproduzir as falas com entonação natural e respostas de texto resumidas na tela.
