# DECISION_LOG.md
# PROFEPLAN V4
## Registro de Decisões Estratégicas e Arquiteturais

Versão: 4.0
Status: Ativo

---

# ADR 001: Arquitetura de IA Separada (Azure vs Gemini)

## Status
Aprovado

## Contexto
O banco de dados Supabase necessita de embeddings estruturados para busca vetorial. Usar modelos da Azure para embeddings e armazenamento vetorial geraria incompatibilidades com os dados originais no Supabase pgvector(768).

## Decisão
Implementamos uma divisão rígida na arquitetura de IA:
1. **Azure OpenAI:** Responsável pela geração de texto rica (planos, PDI, chat, avaliações) centralizada no AiCore.
2. **Google Gemini (text-embedding-004):** Responsável estritamente pela geração de vetores de 768 dimensões para busca de similaridade e RAG no banco de dados.

## Consequências
* Garantia de integridade das tabelas de vetores no Supabase.
* Excelente performance de busca sem risco de crash no banco por dimensões incorretas de vetores.

---

# ADR 002: Filosofia de Divisão "Holding Industrial"

## Status
Aprovado

## Contexto
O processamento e extração de PDFs caóticos do PNLD e currículos escolares exigem alto processamento de CPU e memória, o que sobrecarrega a experiência direta do usuário caso rodasse na mesma aplicação frontend/backend do cliente.

## Decisão
Dividimos o ecossistema em duas macro-camadas:
1. **As Indústrias (Offline):** Pipelines de processamento pesado em Python (ProfeplanHub, Codex, Coletor, Packages) que tratam PDFs, extraem dados e alimentam o banco de forma isolada.
2. **A Loja (Online):** O Web App React e o app móvel Android que apenas consomem esses dados processados e estruturados, provendo alta fluidez e baixo consumo de recursos client-side.

## Consequências
* Separação de responsabilidades.
* Interfaces rápidas e responsivas.
* Escalabilidade horizontal simplificada.

---

# ADR 003: Hierarquia Estrita de Vínculos de Alunos e PDI

## Status
Aprovado

## Contexto
Refatorações anteriores simplificaram os dados de alunos em strings avulsas, quebrando a capacidade do professor de gerar PDIs consistentes baseados no perfil pedagógico de inclusão dos estudantes.

## Decisão
Tornou-se obrigatória a cadeia relacional estrita:
`Escola ↔ Professor ↔ Turma ↔ Aluno ↔ Disciplina`.
O cadastro do aluno deve registrar obrigatoriamente as condições de inclusão (ex: TEA, TDAH, Dislexia) e observações pedagógicas que servem de entrada automatizada (System Prompt) para as solicitações da IA no motor de PDI.

## Consequências
* Restauração da fidelidade do módulo de inclusão.
* PDIs gerados com alto grau de acerto e personalização real.
