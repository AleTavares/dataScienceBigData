# Data Science e Big Data

**MBA — Universidade Presbiteriana Mackenzie**

Disciplina teórica sobre estratégias de dados, ambientes de Big Data, arquiteturas de Data Lake e a abordagem Spec-Driven, orientada a profissionais de negócio e líderes que precisam tomar decisões data-driven.

## Visão Geral do Curso

| Item | Detalhe |
|------|---------|
| Carga horária | 32 horas (8 aulas × 4 horas) |
| Formato | Teoria expositiva + exercício discursivo em grupo ao final de cada aula |
| Linguagem | Português do Brasil |
| Público-alvo | Profissionais de negócio, gestores e líderes (sem foco em programação) |

### Estrutura de cada aula

Cada aula de 4 horas apresenta o conteúdo teórico e termina com um exercício discursivo em grupo, no qual os alunos analisam um caso real e produzem uma análise aplicada ao próprio setor.

| Bloco | Conteúdo | Duração aproximada |
|-------|----------|--------------------|
| Teoria — Parte 1 | Conceito principal | 40 min |
| Teoria — Parte 2 | Aplicação prática | 40 min |
| Intervalo | — | 10 min |
| Teoria — Parte 3 | Aprofundamento / casos setoriais | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real + transferência para o setor | 70 min |
| Encerramento | Síntese e leituras | 20 min |

### Blocos Temáticos

| Bloco | Aulas | Tema |
|-------|-------|------|
| Fundamentos | 1–2 | Big Data, Data Science e estratégia Data-Driven |
| Arquitetura | 3–4 | Data Lake, Data Warehouse e arquiteturas analíticas |
| Governança | 5–6 | Qualidade, governança e privacidade de dados |
| Execução | 7 | Spec-Driven: especificação de projetos de dados |
| Entrega | 8 | Apresentação do trabalho final |

---

## Ementa por Aula

### Aula 1 — O que é Big Data e por que isso muda tudo
- Os 5 V's do Big Data (Volume, Velocidade, Variedade, Veracidade, Valor)
- Dados transacionais (OLTP) vs. analíticos (OLAP)
- Por que ferramentas tradicionais não escalam
- Exercício: Como o iFood usa Big Data

### Aula 2 — Data Science como vantagem competitiva
- Ciclo de vida de um projeto de Data Science (visão executiva)
- Os 4 tipos de análise: descritiva, diagnóstica, preditiva, prescritiva
- Business case e as perguntas certas ao modelo
- Exercício: Nubank e o score de crédito próprio

### Aula 3 — Arquiteturas de dados: do Data Warehouse ao Data Lake
- Evolução: OLTP → DW → Data Lake → Lakehouse
- Diferenças entre Data Warehouse, Data Lake e Lakehouse
- Arquitetura Medallion: Bronze, Silver e Gold
- Exercício: Arquitetura de dados do Mercado Livre

### Aula 4 — Construindo um Data Lake: estratégia e decisões
- Framework de priorização de fontes (valor × complexidade)
- Governança mínima do Dia 1
- Principais riscos e business case
- Exercício: A estratégia de dados da Ambev

### Aula 5 — Qualidade e Confiabilidade dos Dados
- As 6 dimensões de qualidade de dados
- Custo da má qualidade (CODB)
- Data Quality como processo contínuo; catálogo e lineage
- Exercício: Qualidade de dados no DATASUS

### Aula 6 — Governança, Privacidade e LGPD
- Governança de dados e seus papéis (CDO, Data Owner, Steward, DPO)
- LGPD na prática: tipos de dados e bases legais
- Data Mesh: governança distribuída
- Exercício: Processo da ANPD contra a Claro Brasil

### Aula 7 — Spec-Driven: especificação como base de projetos de dados
- Por que especificar antes de executar
- As 3 fases: Requisitos → Design → Tarefas
- Escrevendo requisitos com critérios de aceitação verificáveis
- Exercício: Especificando um projeto de dados do zero

### Aula 8 — Apresentação do Trabalho Final
- Apresentação oral da especificação do projeto (15 min por grupo)
- Entrega do documento escrito
- Critérios de avaliação

---

## Trabalho Final

Desenvolvido em grupos de 3 a 5 pessoas ao longo do curso.

**Entregável:**
1. **Documento escrito** (10–15 páginas): diagnóstico, especificação Spec-Driven (requisitos, design e tarefas), proposta de arquitetura, estratégia de governança e qualidade, e riscos de um projeto de dados para uma organização real ou plausível
2. **Apresentação oral** (15 min + 5 min de perguntas): apresentação da especificação ao professor

Instruções completas em [`aula_08/TRABALHO_FINAL.md`](aula_08/TRABALHO_FINAL.md).

---

## Estrutura do Repositório

```
dataScienceBigData/
├── README.md                    # Este arquivo
├── plano-de-aulas.md            # Plano detalhado de aulas
├── aula_01/                     # O que é Big Data e por que isso muda tudo
│   ├── README.md                # Conteúdo da aula
│   └── aula_01_slides.html      # Slides da aula
├── aula_02/                     # Data Science como vantagem competitiva
├── aula_03/                     # Arquiteturas de dados
├── aula_04/                     # Construindo um Data Lake
├── aula_05/                     # Qualidade e Confiabilidade dos Dados
├── aula_06/                     # Governança, Privacidade e LGPD
├── aula_07/                     # Spec-Driven para projetos de dados
└── aula_08/                     # Apresentação do Trabalho Final
    ├── README.md
    └── TRABALHO_FINAL.md        # Regras de entrega
```

## Licença

Material didático de uso exclusivo para a disciplina Data Science e Big Data do MBA — Universidade Presbiteriana Mackenzie.
