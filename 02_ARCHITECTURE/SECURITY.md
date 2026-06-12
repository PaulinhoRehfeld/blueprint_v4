# SECURITY.md
# PROFEPLAN V4
## Security & Privacy Architecture

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. SEGURANÇA DE DADOS (LGPD)

O PROFEPLAN lida com dados confidenciais de professores e de estudantes da educação básica brasileira (incluindo laudos e observações de necessidades especiais).

Para garantir conformidade com a Lei Geral de Proteção de Dados (LGPD):
* Criptografia AES-256 aplicada no banco de dados para campos sensíveis.
* Row Level Security (RLS) no Supabase, garantindo que um professor só consiga visualizar e gerenciar registros vinculados à sua própria conta e às suas turmas.

---

# 2. PROTEÇÃO DE SEGREDO INDUSTRIAL

Os algoritmos de RAG híbrido educacional, guardrails BNCC e pipeline de normalização PNLD são protegidos legalmente sob a Política de Segredo Industrial da WR TECH.

O código-fonte da aplicação é fechado (Closed Source). Apenas conexões validadas pelo protocolo de Handshake e tokens de integração oficiais do Supabase possuem autorização para dialogar com as APIs do sistema.

---

# 3. SEGURANÇA DE CÓDIGO E PIPELINES

* Autenticação via múltiplos fatores (MFA/2FA) para acessos de infraestrutura administrativa.
* Verificação automática de vulnerabilidades em bibliotecas Python (pip-audit) e pacotes npm (npm audit) antes de qualquer empacotamento ou deploy.
