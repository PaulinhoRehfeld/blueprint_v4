# KPIS.md
# PROFEPLAN V4
## Operational Key Performance Indicators

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

O sucesso do PROFEPLAN V4 baseia-se na entrega de valor mensurável para os professores e escolas. A governança do sistema monitora ativamente indicadores de velocidade, qualidade e economia de tempo.

---

# 2. MÉTRICAS OPERACIONAIS DE NEGÓCIO

## Horas Economizadas por Professor (North Star Metric)
* **Objetivo:** Garantir que o professor economize pelo menos 4 horas semanais de trabalho burocrático utilizando o PROFEPLAN.
* **Medição:** Tempo médio de planejamento de aula reduzido em até 80% em relação ao método manual de consulta à BNCC.

---

# 3. MÉTRICAS DE ENGENHARIA E IA

## Tempo de Geração
* **Plano de Aula Diário:** Menos de 30 segundos utilizando Azure OpenAI centralizado.
* **Planejamento Trimestral RAG:** Menos de 3 minutos, incluindo varredura completa da base de dados e validação BNCC.
* **Geração de PDI:** Menos de 45 segundos por aluno.

---

## Score de Qualidade Pedagógica e Conformidade BNCC
* **Regra de Aceitação:** Todo material gerado (plano ou prova inédita) passa por validadores que calculam um score de fidelidade curricular de 0 a 100.
* **Limite Mínimo:** Qualquer documento gerado com score inferior a 70 é descartado e reiniciado silenciosamente na API da IA.
* **Target:** Manter média de conformidade superior a 90%.
