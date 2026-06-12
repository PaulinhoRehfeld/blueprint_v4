# BACKEND.md
# PROFEPLAN V4
## Backend Architecture (As Indústrias)

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O backend da V4.0 é composto por um conjunto de pipelines robustos de processamento de dados e microsserviços em Python, denominados na filosofia da plataforma como "As Indústrias".

Ele cuida de tarefas pesadas que seriam inviáveis no lado do cliente: extração estruturada de PDFs de currículos, normalização de livros do PNLD, renderização de documentos PDF complexos no servidor e orquestração de múltiplos agentes de inteligência artificial.

---

# 2. ESTRUTURA DOS COMPONENTES

## 2.1 ProfeplanHub
Pipeline integrado de processamento de dados que unifica a extração e indexação de dados educacionais de livros do PNLD.
* **Componentes:** CODEX (indexação estruturada via Gemini), COLETOR (raspador web via Playwright), SMARTCLASS (modelagem e curadoria).

---

## 2.2 rlm (Recursive Language Models)
Framework implementado para gerenciar prompts e fluxos lógicos de chamadas sucessivas (loops de decisão de IA) adaptados para o contexto escolar brasileiro.

---

## 2.3 packages/industry-curriculum
Módulo focado na leitura de PDFs do planejamento trimestral da Secretaria de Educação de Minas Gerais (SEEMG), convertendo dados desestruturados em JSONs rígidos e alinhados à BNCC.

---

## 2.4 packages/industry-pnld
A "refinaria" de livros didáticos. Trata a variação de layouts de editoras diferentes (FTD, Moderna, Ática) e gera chunks normatizados de texto para o RAG.

---

## 2.5 packages/graphics-profeplan
Motor gráfico server-side responsável pela geração final de arquivos DOCX e PDF profissionais a partir de templates do Microsoft Word, utilizando bibliotecas como python-docx e WeasyPrint para manter o layout intocado.

---

# 3. STACK TECNOLÓGICO

* **Linguagem Principal:** Python 3.11+
* **Processamento Assíncrono / Concorrência:** ThreadPoolExecutor, asyncio
* **Automação de Navegador:** Playwright (Chromium headless)
* **Conexão de Dados:** Supabase Python Client
* **Renderização:** WeasyPrint, python-docx-template
