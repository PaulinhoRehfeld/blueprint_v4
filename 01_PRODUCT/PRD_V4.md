# PRD_V4.md
# PROFEPLAN V4
## Product Requirements Document - V4 Core

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

---

# Módulos Funcionais do Sistema

---

## Módulo 1: Configurações, Onboarding e Perfil Profissional

### 1.1 Regra de Primeiro Acesso (Bloqueante)
Se o usuário logado tiver dados de perfil incompletos, a navegação é interceptada e o modal "Configurações > Perfil e Preferências" abre automaticamente. Geração de planos é travada até o preenchimento.

### 1.2 Dados do Perfil e Vínculo Institucional
Campos obrigatórios: Nome Completo, E-mail Institucional, MASP / Matrícula. Suporte a vínculos múltiplos em diferentes escolas.

### 1.3 Busca de Escolas e Regra do INEP
Autocompletar busca escolas pré-cadastradas preenchendo Cidade e Código INEP. Se digitado manualmente, Código INEP fica nulo e a nova escola não é registrada na tabela global, evitando poluição.

### 1.4 Personalização de Documentos (Exportação)
Upload de logo (PNG/JPG) e textos para cabeçalhos/rodapés personalizados que sairão nos PDFs/DOCX gerados.

### 1.5 Preferências de IA (System Prompt)
Configuração do comportamento base da IA: metodologia ativa padrão, estilo pedagógico, foco avaliativo e tom de escrita.

---

## Módulo 2: Minhas Turmas e Gestão de Alunos

### 2.1 Criação de Turmas via PDF
Upload de PDF de Relação Nominal de Alunos. Parser extrai código da escola, identificação da turma, ano letivo, turno e disciplina.

### 2.2 Extração Nominal de Alunos
Cadastro automático separando: Seq (número da chamada), Código (matrícula) e Nome Completo.

### 2.3 Campo "Observações" e Gatilho do PDI
Campo de texto ao lado do nome do aluno para observações de inclusão (laudos de TDAH, TEA, etc). Se preenchido, ativa o vínculo com o módulo PDI.

### 2.4 Portabilidade
Ao transferir o aluno de turma ou ano, o histórico completo (laudos, observações e PDIs) migra junto.

---

## Módulo 3: Planejamento Trimestral e Multi-Agentes

### 3.1 Arquitetura Multi-Agentes
Operado por agentes autônomos (Agente RAG BNCC, Agente PNLD) em loops de validação até conformidade curricular completa.

### 3.2 Guardrails BNCC
Proibição estrita de alucinações de competências ou códigos curriculares.

### 3.3 Integração PNLD
Se selecionado "Utilizar Livro PNLD", a IA vincula capítulos e páginas do livro didático ao plano. Se não encontrado, usa BNCC como fallback e aciona robô de busca.

---

## Módulo 4: Elaboração de Aulas Semanais e Diárias

### 4.1 Varredura de Contexto Trimestral
Antes de gerar a aula diária, a IA lê todo o planejamento trimestral garantindo a continuidade pedagógica e alinhamento cronológico das aulas anteriores e posteriores.

### 4.2 Parâmetros de Entrada
Dados básicos da turma, data da aula e prompt direcional/foco específico inserido pelo professor.

### 4.3 Estrutura de Saída
Cabeçalho, habilidades BNCC reais, objetivos, recursos, desenvolvimento detalhado (Introdução, Desenvolvimento e Fechamento) e avaliação diária.

---

## Módulo 5: Adaptações PDI/DUA

### 5.1 Validação de Dependências
Exige seleção de turmas ativas, filtro de inclusão (apenas alunos com campo "Observações" preenchidos) e seleção da aula a ser adaptada.

### 5.2 Subagente DUA (Desenho Universal para Aprendizagem)
Cruza o perfil do aluno com o plano de aula original e a base de diretrizes RAG, gerando estratégias de ensino adaptadas.

### 5.3 Guardrails de Ética e Privacidade
Os documentos propostos NUNCA expõem termos clínicos, deficiências ou laudos no título ou corpo das atividades, protegendo o aluno contra rotulação.

---

## Módulo 6: Simulados ENEM/Saeb (Banco Estático)

### 6.1 Banco de 17.000 Questões
Tolerância zero para alucinações. IA atua estritamente como bibliotecária de busca sobre a base estática de 17.000 questões pré-cadastradas.

### 6.2 Modos de Busca
Busca manual (palavras-chave, habilidades BNCC) ou Modo Espelho (IA lê o planejamento trimestral e puxa apenas questões sobre conteúdos já ministrados).

### 6.3 Processamento
Seleção manual, balanceamento TRI, geração de versões A/B com gabarito embaralhado e exportação.

---

## Módulo 7: Avaliações Contextualizadas (Criação Inédita)

### 7.1 Fonte de Verdade
IA gera questões inéditas baseada estritamente no planejamento trimestral e nas aulas que o professor de fato documentou como aplicadas.

### 7.2 Níveis de Dificuldade
Input granular do número exato de questões fáceis, médias e difíceis.

### 7.3 Balanceamento de Gabarito
Gabarito com respostas distribuídas aleatoriamente (predominância de no máximo 2 respostas de diferença entre alternativas corretas).

### 7.4 Antifraude
Embaralhamento de questões/alternativas para gerar versões A/B/C com gabarito mestre unificado.

---

## Módulo 8: Meus Arquivos e Gestão de Documentos

### 8.1 Taxonomia e Nomenclatura Automática
Nomes de arquivos padronizados obrigatoriamente:
`[Tipo do Documento] [Número/Referência] - [Tema Específico] - [Disciplina]`.

### 8.2 Modo Foco (Edição)
Ocultação de painéis laterais ao editar, oferecendo tela cheia focada na folha de papel final do documento.

### 8.3 Filtros
Organização por escola, turma e tipo (Plano, Prova, PDI), aplicando cabeçalho e logo oficiais no download.

---

## Módulo 9: FREEDAY - Agente Autônomo de Voz

### 9.1 Botão Global
Agente de voz acessível como botão fixo flutuante em todas as telas e abas do sistema.

### 9.2 Multimodalidade
Speech-to-Text (STT) para receber ordens faladas e Text-to-Speech (TTS) para dar respostas curtas e ler os materiais gerados em voz alta.

### 9.3 Function Calling
O agente pode acionar telas e botões programaticamente (ex: "Exporte esta prova para PDF" ou "Navegue para minhas turmas").

### 9.4 Consciência de Contexto
Injeção silenciosa do estado atual do professor (ex: qual tela/aluno está aberto) para permitir ordens relativas como "Refaça o segundo parágrafo".

---

## Módulo 10: Gestão de Documentos Pessoais & Agentes Customizados

### 10.1 Nova Área "Meus Documentos"
Espaço dedicado onde o professor pode enviar arquivos PDF e associá-los a uma das três categorias de contextualização:
* **Plano de Curso:** Documento normativo de maior prioridade.
* **Livro:** Livro texto ou referencial de apoio.
* **Material Didático:** Apostilas, slides, artigos e textos de apoio.

### 10.2 Pipeline de Ingestão e Processamento
O fluxo de processamento de novos arquivos segue o pipeline:
`Upload PDF ➔ Extração OCR/Text ➔ Conversão para Markdown ➔ Validação pelo Professor ➔ Base Oficial ➔ Agente Especializado`.

* **Saída Gerada:** Um arquivo markdown estruturado (ex: `historia_1ano.md`) salvo com os metadados do professor, disciplina e prioridade do documento.

### 10.3 Versionamento de Documentos
Toda atualização de documento não sobrescreve a versão anterior. O sistema cria e cataloga novas versões (`V1`, `V2`, `V3`) de forma transparente (ex: `História 2026 V1`, `História 2026 V2`).

### 10.4 Painel de Aprovação de Markdown
Para mitigar falhas comuns de OCR em tabelas ou PDFs corrompidos, o professor visualiza o Markdown bruto gerado e dispõe dos botões:
* **✓ Aprovar:** Homologa o documento para a base oficial de contexto.
* **✗ Reprocessar:** Re-executa o parser com parâmetros ajustados.

### 10.5 Extração Automatizada de Metadados e Score de Confiança
* **Filtros Inteligentes:** Extração automática de metadados durante a ingestão (Disciplina, Ano, Carga Horária, Competências, Habilidades e Objetos de Conhecimento).
* **Qualidade de Extração:** Exibição de um score de confiança em percentual. Se for menor que 80%, o sistema emite um alerta sugerindo revisão manual pelo professor.

### 10.6 Agente de Curadoria Automática
Processo de curadoria assistido por IA secundária para apontar capítulos faltantes, tabelas quebradas ou quebras de formatação graves, gerando um relatório sutil na tela de aprovação.

### 10.7 Criação do Agente Especializado da Disciplina
Após aprovação do Markdown oficial do plano de curso, o sistema ativa um Agente de IA específico para a turma e disciplina (ex: `Agent_Historia_1Ano_Paulinho`).
Este agente é instanciado com o System Prompt:
`"Você deve utilizar prioritariamente o plano de curso oficial desta disciplina."`

### 10.8 Bloqueio Inteligente de Respostas Fora do Plano
Caso o professor solicite a elaboração de conteúdos ou avaliações sobre temas não previstos no plano de curso oficial homologado, a IA intercepta a requisição e apresenta um aviso:
`"Este tema não foi localizado no plano de curso oficial. Deseja continuar mesmo assim?"`
Com os botões: **Continuar** ou **Cancelar**.

