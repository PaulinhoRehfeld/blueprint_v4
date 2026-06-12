# DATABASE.md
# PROFEPLAN V4
## Database Architecture & Schema

Versão: 4.0
Status: Ativo
Última Atualização: Fevereiro/2026

Banco de Dados: Supabase (PostgreSQL 15)
Extensões: pgvector, uuid-ossp, pgcrypto

---

# 1. VISÃO GERAL

O banco de dados do PROFEPLAN V4 é centralizado no Supabase. Ele implementa o isolamento de dados do professor por meio de diretrizes rígidas de Row Level Security (RLS) do PostgreSQL, garantindo a privacidade e a segurança exigidas pela LGPD.

Além de persistir dados transacionais simples, ele armazena os embeddings vetoriais de 768 dimensões usados no RAG da plataforma.

---

# 2. HIERARQUIA RELACIONAL OBRIGATÓRIA

```text
Escola (Código INEP)
  └── Professor
        └── Turma (classes)
              ├── Aluno (students) ↔ Observações Pedagógicas (Inclusão)
              └── Disciplina
```

---

# 3. PRINCIPAIS TABELAS E SCHEMAS

## classes (Turmas)
Tabela que armazena as turmas criadas ou importadas pelo professor.
```sql
CREATE TABLE classes (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  school_id UUID REFERENCES schools(id),
  name TEXT NOT NULL, -- Ex: "1º EM REG 1"
  grade TEXT, -- Ano/Série
  shift TEXT, -- Turno (Manhã, Tarde, Integral)
  academic_year INTEGER DEFAULT 2026,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT timezone('utc'::text, now())
);
```

---

## students (Alunos)
Tabela vital para o ecossistema de educação especial e inclusiva.
```sql
CREATE TABLE students (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  class_id UUID REFERENCES classes(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  registration_code TEXT, -- Matrícula / Código SIMADE
  birth_date DATE,
  status TEXT DEFAULT 'active',
  observations TEXT, -- Metadados cruciais de Inclusão (laudos, TEA, TDAH, Dislexia)
  created_at TIMESTAMP WITH TIME ZONE DEFAULT timezone('utc'::text, now())
);
```

---

## pdi_documents (PDIs Gerados)
```sql
CREATE TABLE pdi_documents (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  student_id UUID REFERENCES students(id) ON DELETE CASCADE,
  teacher_id UUID NOT NULL,
  content JSONB NOT NULL, -- Dados estruturados do plano adaptado
  created_at TIMESTAMP WITH TIME ZONE DEFAULT timezone('utc'::text, now())
);
```

---

## embeddings (Busca Vetorial)
Tabela que armazena os vetores gerados a partir da BNCC e livros didáticos do PNLD.
```sql
CREATE TABLE embeddings (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  content TEXT NOT NULL, -- Conteúdo bruto do fragmento
  embedding VECTOR(768) NOT NULL, -- IMPORTANTE: Vetores de 768 dimensões
  metadata JSONB, -- Informações de capítulo, livro, BNCC
  created_at TIMESTAMP WITH TIME ZONE DEFAULT timezone('utc'::text, now())
);
```

---

# 4. DIRETRIZ VETORIAL (IMPORTANTE)

O tamanho do vetor na V4 é **estritamente** configurado como `VECTOR(768)`. Isto se deve ao uso do modelo de embeddings da Google (`text-embedding-004`).

Nenhuma refatoração ou migração deve alterar esta dimensionalidade sob o risco de quebrar as consultas do RAG Pedagógico no banco Supabase.
