# TECHNICAL_DEBT.md
# PROFEPLAN V4
## Technical Debt & Code Deadweight

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O desenvolvimento acelerado da V4 do PROFEPLAN resultou em redundâncias no código-fonte, módulos legados não utilizados e dependências desatualizadas.

Este documento cataloga a dívida técnica mapeada para saneamento imediato antes da migração para a V5.

---

# 2. INVENTÁRIO DE CÓDIGO MORTO

Conforme mapeado no inventário arqueológico do repositório (`INVENTARIO_CODIGO_MORTO.md`):
* Módulos antigos de PDF parser no frontend que foram substituídos pelas pipelines Python.
* Scripts de migração de banco temporários duplicados na pasta `scripts` e `infra`.
* Código legado da pasta `legacy-web-legacy` que não está sendo referenciado ou importado pelo build atual.

---

# 3. SUMÁRIOS DE REFATORAÇÃO

Com base no relatório de refatoração (`SUMARIO_EXECUTIVO_REFATORACAO.md`):
* **Tipagem Estrita:** Necessidade de reforçar as definições e tipos do TypeScript para as tabelas `students`, `classes` e `pdi_documents` no frontend para evitar o uso excessivo de `any`.
* **Centralização do AiCore:** Migrar chamadas espalhadas da Azure OpenAI para o microsserviço unificado no backend, impedindo chaves expostas ou payloads fora do padrão de validação BNCC.
* **Resolução de Linting:** O arquivo `lint_errors.log` registra múltiplos erros de formatação e variáveis não utilizadas que degradam o tempo de build do Vite.
