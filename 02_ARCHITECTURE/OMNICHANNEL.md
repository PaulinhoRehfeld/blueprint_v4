# OMNICHANNEL.md
# PROFEPLAN V4
## Omnichannel Architecture

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O PROFEPLAN V4 foi projetado para atuar nos canais onde o professor executa suas atividades pedagógicas no dia a dia: no computador da escola e no smartphone.

A arquitetura garante sincronização em tempo real e portabilidade dos recursos em diferentes telas.

---

# 2. CANAIS DA VERSÃO 4.0

## 2.1 Web App (Desktop)
Interface completa voltada para tarefas de grande porte que exigem foco, como elaboração de planejamentos trimestrais completos, gestão de turmas e exportação de avaliações.

---

## 2.2 Mobile App (Android)
Aplicativo empacotado nativamente via Capacitor a partir da base React/TS. O aplicativo móvel foca na rapidez de uso e consulta pelo professor em sala de aula.
* **Recursos prioritários no mobile:** Assistente de voz FREEDAY, consulta rápida a planos de aula do dia e checagem de observações de alunos.

---

# 3. SINCRONIZAÇÃO DE DADOS

O banco de dados relacional e a camada de autenticação unificada do Supabase garantem que qualquer alteração feita no Web App reflita instantaneamente no celular do professor, e vice-versa.
* **Gerenciamento de Arquivos:** Uploads de logos institucionais e fotos são armazenados no Supabase Storage e servidos de forma otimizada para todas as plataformas através de CDNs rápidas.
* **Segurança Móvel:** Sessões criptografadas mantidas de forma segura pelo Keytar / armazenamento seguro nativo do aparelho em conformidade com RLS.
