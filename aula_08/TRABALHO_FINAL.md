# Trabalho Final — Data Science e Big Data

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Entrega:** Início da Aula 8
**Apresentação:** Durante a Aula 8

---

## Objetivo

O trabalho final consolida o aprendizado do curso, aplicando os conceitos de Big Data, Data Science, arquiteturas de dados, qualidade, governança e a abordagem Spec-Driven à especificação de um projeto de dados para uma organização real ou plausível escolhida pelo grupo.

---

## Formação dos Grupos

- **Tamanho:** 3 a 5 integrantes
- **Formação:** livre, definida até a Aula 3
- **Organização-alvo:** cada grupo escolhe uma organização diferente (sem repetição de setor, se possível)

---

## A Organização-Alvo

O grupo deve escolher **uma organização** para estudar. Pode ser:
- Uma empresa real onde algum integrante trabalha (dados confidenciais devem ser anonimizados)
- Uma empresa pública de referência no setor de atuação do grupo
- Uma empresa plausível criada pelo grupo (detalhada o suficiente para ser crível)

**Setores sugeridos** (não obrigatórios): saúde, varejo, financeiro, logística, educação, governo, indústria, agronegócio, telecomunicações.

---

## Estrutura do Documento Escrito

**Extensão:** 10 a 15 páginas (excluindo capa, sumário e referências)
**Formato:** ABNT ou livre, desde que consistente

### Seções obrigatórias:

#### 1. Apresentação da Organização e do Problema (1–2 páginas)
- Descrição da empresa: setor, porte, produtos/serviços, clientes
- Contexto competitivo e desafios atuais
- Qual decisão de negócio está sendo tomada mal ou tarde demais hoje por falta de dados?

#### 2. Diagnóstico e Fontes de Dados (1–2 páginas)
- As 3 maiores deficiências analíticas atuais da organização
- Mapeamento das principais fontes de dados existentes
- Que tipo de análise (descritiva, diagnóstica, preditiva, prescritiva) o projeto exige? (Aula 2)

#### 3. Especificação Spec-Driven — Requisitos (2–3 páginas)
- Pergunta de negócio central do projeto
- Ao menos 4 requisitos no formato "história de usuário + critérios de aceitação verificáveis" (Aula 7)
- Restrições do projeto: prazo, orçamento, LGPD, qualidade mínima de dados

#### 4. Especificação Spec-Driven — Design (2–3 páginas)
- Qual arquitetura é recomendada: Data Warehouse, Data Lake ou Lakehouse? Justifique. (Aula 3)
- Diagrama simplificado da arquitetura proposta
- As fontes de dados prioritárias (framework de priorização da Aula 4)
- Arquitetura Medallion: quais dados iriam para cada camada e por quê?
- Estratégia de qualidade (Aula 5) e governança/LGPD (Aula 6): dimensões críticas, Data Owners e política de acesso

#### 5. Especificação Spec-Driven — Plano de Tarefas (1–2 páginas)
- Decomposição do design em tarefas concretas, ordenadas por dependência
- Cada tarefa deve ser pequena, rastreável a um requisito e ter critério de conclusão
- Identificação da primeira entrega de valor (o que estará pronto primeiro)

#### 6. Riscos e Mitigação (1 página)
- Os 3 maiores riscos do projeto (técnicos, de dados ou organizacionais)
- Estratégia de mitigação para cada um

---

## Apresentação Oral

**Duração:** 15 minutos de apresentação + 5 minutos de perguntas
**Formato:** Slides (PowerPoint, Google Slides ou equivalente)
**Dinâmica:** O grupo apresenta a especificação ao professor, que avalia e faz perguntas ao final.

### Estrutura sugerida dos slides (máx. 15 slides):

| # | Slide | Conteúdo |
|---|-------|---------|
| 1 | Capa | Empresa, grupo, data |
| 2 | O problema | Qual decisão está sendo tomada mal hoje? |
| 3 | Diagnóstico e fontes de dados | Deficiências e fontes mapeadas |
| 4–6 | Requisitos | Pergunta de negócio + requisitos com critérios de aceitação |
| 7–9 | Design | Arquitetura + Medallion + qualidade e governança |
| 10–11 | Plano de tarefas | Decomposição e primeira entrega de valor |
| 12 | Riscos | Top 3 riscos e mitigações |
| 13 | Conclusão | Por que essa especificação reduz o risco do projeto? |
| 14–15 | Perguntas | Abertura para perguntas do professor |

---

## Critérios de Avaliação

| Critério | Peso | Descrição |
|----------|------|-----------|
| **Diagnóstico e contexto** | 20% | Clareza do problema, realismo do diagnóstico, fontes de dados mapeadas com critério |
| **Proposta de arquitetura** | 25% | Adequação da arquitetura ao contexto, justificativa bem fundamentada, aplicação da arquitetura Medallion |
| **Governança e qualidade** | 20% | Papéis definidos, impactos de LGPD endereçados, estratégia de qualidade coerente |
| **Especificação Spec-Driven** | 20% | Requisitos verificáveis, design coerente com os requisitos e plano de tarefas incremental |
| **Apresentação oral** | 15% | Clareza, objetividade, capacidade de resposta às perguntas do professor |

**Nota mínima para aprovação:** 7,0 (ponderação definida pelo professor conforme regras da disciplina)

---

## Checklist de Entrega

Antes de entregar, verifique:

- [ ] Documento tem entre 10 e 15 páginas
- [ ] Todas as 6 seções obrigatórias estão presentes
- [ ] A organização-alvo e o problema de negócio estão claramente descritos
- [ ] As principais fontes de dados foram mapeadas
- [ ] A especificação tem ao menos 4 requisitos com critérios de aceitação verificáveis
- [ ] A arquitetura proposta tem diagrama visual e justificativa
- [ ] As fontes de dados foram priorizadas com o framework da Aula 4
- [ ] A arquitetura Medallion foi aplicada com exemplos concretos
- [ ] Os impactos de LGPD e a estratégia de qualidade foram tratados
- [ ] O plano de tarefas é incremental e rastreável aos requisitos
- [ ] Os 3 maiores riscos foram identificados com mitigação
- [ ] Os slides estão prontos e o grupo ensaiou no tempo de 15 minutos

---

## Dúvidas e Orientação

Em caso de dúvidas sobre o trabalho, o professor estará disponível:
- Durante os minutos de encerramento de cada aula
- Por e-mail institucional (consulte o professor para o canal preferido)
- Office hours opcionais (a combinar na Aula 5)

O trabalho final é uma oportunidade de aplicar *tudo* o que foi discutido ao longo do curso em um contexto real e relevante para a sua carreira. Escolha uma organização que realmente importa para você — a qualidade do trabalho será proporcional ao engajamento do grupo com o problema.

Boa sorte!
