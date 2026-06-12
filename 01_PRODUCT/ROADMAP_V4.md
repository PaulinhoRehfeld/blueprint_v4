# ROADMAP_V4.md
# PROFEPLAN V4
## Histórico Evolutivo e Baseline de Desenvolvimento

Versão: 4.0
Status: Concluído
Última Atualização: Fevereiro/2026

---

# Fases do Ciclo de Vida V4.x

---

## Fase 1: Fundação e RAG Local (Q1-Q2 2025)

* Implementação do banco de dados relacional Supabase.
* Configuração da extensão pgvector para armazenamento de embeddings do Gemini.
* Criação das primeiras pipelines de raspagem de currículos estaduais (Minas Gerais).
* Lançamento do gerador de planos de aula diários integrados à BNCC.

---

## Fase 2: Normalização PNLD e PDF Parser (Q3 2025)

* Criação da pipeline **Codex** e do **Coletor** para ingestão estruturada de livros didáticos PNLD de variadas editoras.
* Lançamento do recurso de importação de turmas através do PDF nominal de alunos (SIMADE).
* Estruturação da tabela de alunos e campos de laudos pedagógicos para educação especial.

---

## Fase 3: Inclusão Avançada e DUA (Q4 2025)

* Implementação do módulo PDI baseado nas diretrizes de Desenho Universal para Aprendizagem (DUA).
* Regras estritas de segurança de dados do aluno (criptografia e sigilo na exportação de planos adaptados).
* Integração de loops de feedback do professor nas respostas de IA (Verification Loops).

---

## Fase 4: OMNICHANNEL & FREEDAY (Q1 2026)

* Integração do app mobile Android via Capacitor.
* Lançamento do assistente de voz **FREEDAY** (STT/TTS e function calling).
* Consolidação do banco de dados estático de 17.000 questões do ENEM/Saeb com balanceamento TRI.
* Estabilização de segurança em Row Level Security (RLS) multitenant.

---

# Próximos Passos (Transição para V5)

* Migração da infraestrutura local/Supabase gerenciado para serviços nativos AWS (AWS RDS, AWS ECS, AWS Bedrock).
* Expansão da capacidade de múltiplos canais (WhatsApp e Telegram).
* Evolução da arquitetura de agentes para RLM (Recursive Language Models).
