# PROFEPLAN V4
## Documentation Index

Versão: 4.0

Status:
Official Documentation Hub (V4 Legacy Baseline)

Última Atualização:
Fevereiro/2026

Empresa:
WR TECH AI

Produto:
PROFEPLAN (V4)

---

# VISÃO GERAL

O PROFEPLAN V4 é um ecossistema SaaS de Inteligência Artificial voltado para a educação básica. Seu objetivo é eliminar a sobrecarga burocrática dos professores através da geração automatizada de planos de aula, avaliações e adaptações curriculares (PDI), com alinhamento rigoroso à Base Nacional Comum Curricular (BNCC) e ao Programa Nacional do Livro e do Material Didático (PNLD).

A arquitetura do PROFEPLAN V4 segue uma filosofia "Holding Industrial", com separação rigorosa entre processamento de dados offline em pipelines Python (As Indústrias) e a interface do usuário em React/Capacitor (A Loja).

---

# MISSÃO

Devolver tempo aos professores.

---

# NORTH STAR METRIC

Horas economizadas por professor.

---

# TESES CENTRAIS

Context First

Teacher Memory

Institution Memory

Holding Industrial Architecture

RAG Híbrido Educacional

Professor no Centro

---

# ESTRUTURA DOCUMENTAL

```text
docs/blueprint/

00_VISION/
01_PRODUCT/
02_ARCHITECTURE/
03_DESIGN/
04_EXECUTION/
05_BUSINESS/
```

---

# 00_VISION

Define a direção estratégica e decisões fundacionais da V4.

---

## Arquivos

### VISION.md

Documento de visão estratégica e tese central da versão 4.0.

---

### DECISION_LOG.md

Registro oficial das decisões estratégicas e arquiteturais da V4.

---

# 01_PRODUCT

Define o escopo funcional e o roadmap do produto V4.

---

## Arquivos

### PRD_V4.md

Product Requirements Document (Módulos 1 a 9 da V4).

---

### ROADMAP_V4.md

Planejamento evolutivo e releases da versão 4.0.

---

# 02_ARCHITECTURE

Define a arquitetura técnica detalhada da V4.

---

## FRONTEND.md

Arquitetura frontend (React + Capacitor).

---

## BACKEND.md

Arquitetura backend (pipelines Python e processamento offline).

---

## DATABASE.md

Arquitetura de dados (Supabase PostgreSQL + pgvector 768).

---

## AI_LAYER.md

Arquitetura de inteligência artificial (Azure OpenAI + Gemini text-embedding-004).

---

## AI_GOVERNANCE.md

Guardrails e Scoring BNCC.

---

## SECURITY.md

Políticas de segurança, RLS e segredo industrial.

---

## OMNICHANNEL.md

Funcionamento multicanal (Web e Mobile Android).

---

## AGENTS_CATALOG.md

Catálogo de agentes autônomos (FREEDAY voz, AgentePedagogo, etc.).

---

## INTEGRATIONS.md

Integrações de dados (SIMADE, INEP, Handshake).

---

# 03_DESIGN

Define a experiência visual e a interface com o professor.

---

## DESIGN_SYSTEM.md

Princípios do sistema de design baseado em TailwindCSS.

---

## TOKENS.md

Tokens de estilo e paletas visuais.

---

## UX_GUIDELINES.md

Diretrizes de usabilidade e Modo Foco.

---

# 04_EXECUTION

Define a governança operacional e o histórico do código.

---

## MASTER_BACKLOG.md

Backlog de atividades executadas e pendentes na V4.

---

## RELEASE_PLAN.md

Planejamento de entrega de patches e minor versions.

---

## TECHNICAL_DEBT.md

Dívida técnica e inventário de código morto da V4.

---

## DOCUMENT_AUDIT.md

Auditoria de arquivos e integridade de código.

---

## KPIS.md

Indicadores operacionais e score de geração.

---

# 05_BUSINESS

Define o modelo de negócios e posicionamento estratégico da V4.

---

## PITCH.md

Narrativa B2B/B2G da V4.

---

## COMPETITORS.md

Análise dos concorrentes nacionais.

---

## STARTUPS_PROGRAMS.md

Programas de aceleração e incentivo.

---

# CONCLUSÃO

Este INDEX representa o ponto único de entrada para toda a documentação oficial da versão 4.0 do PROFEPLAN.
