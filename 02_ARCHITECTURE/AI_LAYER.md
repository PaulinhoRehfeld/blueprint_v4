# AI_LAYER.md
# PROFEPLAN V4
## AI Layer Architecture

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

A camada de inteligência artificial do PROFEPLAN V4 é baseada em uma arquitetura híbrida de múltiplos provedores de modelos fundacionais.

Esta divisão otimiza os custos e o tempo de resposta, além de garantir a estabilidade relacional do banco de dados vetorial.

---

# 2. FLUXO HÍBRIDO DE MODELOS

```text
       [ AÇÃO DO PROFESSOR ]
                 │
        ┌────────┴────────┐
        ▼                 ▼
  [ Busca/RAG ]     [ Geração Texto/PDI ]
        │                 │
  Google Gemini     Azure OpenAI
  text-embedding-   gpt-4o / gpt-35-turbo
  004 (768 dims)          │
        │                 ▼
        ▼           [ Retorno do Texto ]
  [ Supabase pgvector ]
```

---

# 3. COMPONENTES

## 3.1 Geração de Conteúdo (Azure OpenAI)
Responsável pelas tarefas generativas críticas que exigem formatação estrita, lógica educacional refinada e baixo tempo de resposta:
* Planos de aula trimestrais, semanais e diários.
* Geração de questões inéditas para avaliações.
* Geração do Plano de Desenvolvimento Individual (PDI) com adaptação DUA.
* Chat e interações com a assistente pedagógica.

---

## 3.2 Busca Semântica e RAG (Google Gemini)
Responsável pelo pipeline de recuperação baseada em contexto (Retrieval-Augmented Generation):
* **Modelo:** `text-embedding-004`.
* **Saída:** Embeddings estáveis de 768 dimensões.
* Indexação de materiais da BNCC e conteúdos do PNLD no banco Supabase.

---

## 3.3 Pipeline de Ingestão de Livros (Gemini 2.0 Flash)
Utilizado de forma assíncrona ("Indústrias") para extrair texto bruto e metadados estruturados dos PDFs de livros pedagógicos enviados para a plataforma.

---

# 4. MOTOR DO PDI (INCLUSÃO)

O prompt de geração enviado à Azure OpenAI no módulo PDI é dinâmico. O sistema intercepta a chamada de geração da aula, localiza o aluno selecionado no banco, puxa seus metadados de inclusão (laudos de autismo, TDAH, deficiências) do campo `observations` e concatena essas regras ao System Prompt.

O modelo gera estratégias educacionais que cobrem a mesma habilidade da BNCC, mas modificam a abordagem pedagógica, ferramentas de avaliação e limites de tempo conforme a necessidade do estudante.
