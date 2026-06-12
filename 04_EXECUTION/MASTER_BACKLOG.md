# MASTER_BACKLOG.md
# PROFEPLAN V4
## Master Backlog

Versão: 4.0
Status: Ativo (Manutenção de Baseline)
Última Atualização: Fevereiro/2026

---

# 1. ATIVIDADES CONCLUÍDAS

* **[CORE]** Integração do backend em Python com o Supabase Client.
* **[RAG]** Normalização de vetores de 768 dimensões usando `text-embedding-004`.
* **[IMPOR]** Leitor de PDF do SIMADE para cadastro automático de alunos e turmas.
* **[PDI]** Filtro de alunos inclusivos no módulo de PDI baseado no campo `observations`.
* **[VOZ]** Componente global e function calling do assistente de voz FREEDAY.
* **[PROV]** Banco de dados estático de 17.000 questões do ENEM/Saeb integrado sem alucinação.

---

# 2. ATIVIDADES EM ANDAMENTO (MIGRAÇÃO & CORREÇÕES)

* **[BUG]** Restauração completa de vínculos relacionais corrompidos entre Alunos, observações e documentos de PDI no banco de dados.
* **[INFRA]** Ajustes de Row Level Security (RLS) no Supabase para isolar turmas compartilhadas entre professores.
* **[LINT]** Limpeza geral de arquivos mortos e otimização do build bundle no frontend Vite.

---

# 3. BACKLOG DE MELHORIAS (PRÉ-V5)

* **[IA]** Integração experimental com modelos Claude 3.5 Sonnet para avaliação pedagógica complexa.
* **[MÓVEL]** Otimização de performance de áudio do FREEDAY em celulares Android antigos rodando Capacitor.
