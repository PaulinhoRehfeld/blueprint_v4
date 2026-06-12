# AGENTS_CATALOG.md
# PROFEPLAN V4
## Catalog of Autonomous Agents

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O ecossistema do PROFEPLAN V4 utiliza agentes de inteligência artificial autônomos e focados em tarefas específicas.

Estes agentes orquestram buscas, validam regras curriculares e interagem diretamente com o usuário por voz ou texto.

---

# 2. CATÁLOGO DOS AGENTES V4

## 2.1 Agente Pedagogo (Core)
Responsável por estruturar a escrita dos planejamentos de aula e avaliações. Ele combina as preferências de estilo do professor, as habilidades da BNCC e o histórico de aulas anteriores no prompt final para a Azure OpenAI.

---

## 2.2 Agente RAG BNCC
Agente especialista em buscar semelhanças e correlações na base de dados do Supabase. Ele localiza as habilidades específicas da BNCC correspondentes ao tema solicitado pelo professor, impedindo alucinações de competências.

---

## 2.3 Agente PNLD
Agente focado na leitura estruturada de livros didáticos. Ele extrai de forma assíncrona informações de ISBN, páginas e capítulos de livros digitais e os correlaciona de forma lógica aos planejamentos trimestrais gerados.

---

## 2.4 Assistente FREEDAY
Agente de voz omnipresente na interface. Ele atua sob o modelo de *Function Calling* e *Context Awareness*:
* **Multimodalidade:** Realiza Speech-to-Text (STT) e Text-to-Speech (TTS).
* **Navegação Autônoma:** Executa comandos do tipo "Abra minhas turmas" ou "Exporte esta avaliação" sem que o usuário use o mouse.
* **Injeção de Estado:** Recebe silenciosamente a informação visual de qual tela o professor está usando para compreender comandos relativos como "Refaça este parágrafo".
