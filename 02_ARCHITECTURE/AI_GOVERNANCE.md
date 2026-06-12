# AI_GOVERNANCE.md
# PROFEPLAN V4
## AI Governance & Guardrails

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# 1. VISÃO GERAL

A inteligência artificial aplicada à educação básica deve seguir princípios éticos rígidos e conformidade legal rigorosa.

O PROFEPLAN V4 implementa barreiras de segurança ativa (guardrails) e regras éticas para evitar alucinações de códigos escolares e proteger a privacidade do estudante.

---

# 2. DIRETRIZES ÉTICAS E DE PRIVACIDADE

## Proteção e Privacidade (Não-Exposição do Aluno)
Nas adaptações de PDI e DUA, a IA está terminantemente proibida de citar explicitamente o termo clínico, diagnóstico, transtorno ou deficiência do estudante no título ou corpo das atividades propostas.

O foco deve ser 100% na estratégia pedagógica de acessibilidade e adaptação metodológica (ex: maior espaçamento de linhas, uso de recursos visuais, tempos diferenciados). Isso previne a rotulação e a exposição desnecessária caso terceiros leiam o material impresso.

---

# 3. GUARDAILS DE CONFORMIDADE CURRICULAR

## Fidelidade à BNCC
Tolerância zero para alucinações em planejamentos curriculares. Os agentes autônomos que validam o planejamento trimestral são programados para auditar as habilidades geradas em relação a uma base de dados oficial estática da BNCC de 2018 (MEC).

Se um código ou habilidade gerado for inválido ou inexistente, o sistema rejeita o planejamento e aciona o Verification Loop para correção da resposta.

---

# 4. CRITÉRIOS DE AVALIAÇÃO

## Matriz de Dificuldade
A IA geradora de avaliações inéditas deve respeitar estritamente a proporção de questões (Fáceis, Médias, Difíceis) definidas pelo professor na interface.

---

## Balanceamento Estatístico
A distribuição de alternativas de respostas corretas deve ser uniforme, limitando a predominância de uma alternativa correta (A, B, C, D ou E) a no máximo duas questões de diferença em relação às demais.
