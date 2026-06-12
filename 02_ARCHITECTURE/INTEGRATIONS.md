# INTEGRATIONS.md
# PROFEPLAN V4
## Integrations & Protocols

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O PROFEPLAN V4 integra fontes de dados governamentais e de mercado para acelerar o fluxo de planejamento e garantir a autenticidade dos dados pedagógicos.

---

# 2. PROTOCOLO HANDSHAKE

O **Handshake Protocol** (especificado no arquivo `HANDSHAKE_PROTOCOL.md` do repositório) define a comunicação de segurança e sincronização entre "As Indústrias" (Python) e "A Loja" (React/TS).

Ele assegura a transferência segura de JSONs de dados escolares, validação de chaves de API em tempo de execução e integridade dos bancos de dados antes de processar requests de RAG pesado.

---

# 3. INTEGRAÇÃO INEP (BUSCA DE ESCOLAS)

O banco de dados do PROFEPLAN V4 possui um cadastro nacional básico de escolas atrelado aos códigos INEP do MEC.

* **Fluxo:** O frontend realiza requisições de autocompletar. Ao selecionar uma escola, o sistema herda Cidade, Estado e Código INEP correspondentes.
* **Regra de Sujeira:** Se a escola digitada pelo professor não constar na base, ele pode concluir o cadastro manual, mas o sistema salva o campo INEP como `null` e mantém a string local apenas no perfil do usuário, impedindo que nomes digitados de forma incorreta poluam a tabela global de escolas da plataforma.

---

# 4. PARSER DE RELAÇÃO NOMINAL SIMADE

Importação automática de turmas através do upload de arquivos de exportação em PDF do SIMADE (Sistema de Registro Escolar de Minas Gerais).

* **Processamento:** O backend lê o PDF, identifica a cabeçalho da escola, ano, turno e disciplina. Em seguida, processa a lista nominal de alunos de forma sequencial salvando número de chamada, código do aluno e nome completo nas tabelas correspondentes.
