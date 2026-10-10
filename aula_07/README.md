# Aula 7 — Spec-Driven: Especificação como Base de Projetos de Dados

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Explicar o que é a abordagem Spec-Driven (orientada por especificação) e por que ela reduz o risco em projetos de dados
2. Diferenciar as três fases de uma especificação de projeto de dados: Requisitos → Design → Tarefas
3. Escrever requisitos claros e verificáveis para uma iniciativa de dados usando critérios de aceitação
4. Avaliar criticamente por que a maioria dos projetos de dados falha por ausência de especificação, não por falha técnica
5. Estruturar a especificação de um projeto de dados antes de qualquer execução

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Por que especificar antes de executar | O problema do "código primeiro" em projetos de dados | 40 min |
| Teoria — As 3 fases da especificação | Requisitos → Design → Tarefas | 40 min |
| Intervalo | — | 10 min |
| Teoria — Escrevendo bons requisitos | Critérios de aceitação verificáveis e rastreabilidade | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Especificação de um projeto de dados real | 70 min |
| Encerramento | Síntese do curso e orientações para o trabalho final | 20 min |

---

## Conteúdo Teórico

### 1. Por que Especificar Antes de Executar

A maioria dos projetos de dados que fracassa não falha por limitação técnica — falha porque ninguém definiu com clareza o que deveria ser construído e por quê. A abordagem **Spec-Driven** (orientada por especificação) inverte a lógica tradicional do "vamos começar a construir e descobrir o que precisamos no caminho".

#### O problema do "execução primeiro"

| Sintoma | O que acontece | Custo |
|---------|---------------|-------|
| Começar pelos dados, não pela pergunta | Pipeline construído sem um propósito de negócio claro | Meses de trabalho sem decisão tomada |
| Requisitos implícitos na cabeça de uma pessoa | Cada integrante entende o projeto de forma diferente | Retrabalho, conflitos, entregas que não servem |
| Sem critério de "pronto" | Ninguém sabe quando o projeto está concluído | Escopo infinito, orçamento estourado |
| Design decidido durante a execução | Decisões de arquitetura tomadas sob pressão | Dívida técnica, decisões difíceis de reverter |

#### A proposta do Spec-Driven

Spec-Driven significa produzir uma **especificação explícita e acordada** antes de executar. A especificação é um documento vivo que:

- Formaliza **o que** será construído (requisitos) antes de decidir **como** (design)
- Estabelece acordo entre negócio e time técnico sobre o resultado esperado
- Permite revisar e corrigir rumo antes de gastar recursos na execução
- Serve como contrato de verificação: o projeto está pronto quando atende à especificação

> Em projetos de dados, especificar antes de executar é o equivalente a definir a pergunta de negócio antes de coletar os dados (Aula 2) e priorizar as fontes antes de ingerir (Aula 4). Spec-Driven é a disciplina que amarra tudo isso em um processo repetível.

---

### 2. As 3 Fases de uma Especificação

A abordagem Spec-Driven organiza o planejamento de um projeto em três fases sequenciais, cada uma com um artefato próprio. Cada fase só avança quando há acordo sobre a anterior.

```
FASE 1              FASE 2              FASE 3
REQUISITOS   ──►    DESIGN       ──►    TAREFAS
"O quê e        "Como vamos         "Em que passos
 por quê?"       construir?"          vamos executar?"
```

#### Fase 1 — Requisitos ("o quê e por quê")

Define o problema de negócio e o resultado esperado, sem decidir ainda a solução técnica.

- Qual pergunta de negócio o projeto responde?
- Quem são os usuários e o que precisam?
- Quais são os critérios de aceitação (como saberemos que está pronto?)
- Quais restrições existem (prazo, orçamento, LGPD, qualidade mínima)?

#### Fase 2 — Design ("como")

Define a solução técnica e as decisões de arquitetura — a partir dos requisitos já acordados.

- Qual arquitetura de dados será usada (DW, Data Lake, Lakehouse — Aula 3)?
- Quais fontes serão ingeridas e em qual ordem (priorização — Aula 4)?
- Como as camadas Medallion serão organizadas?
- Como a qualidade (Aula 5) e a governança (Aula 6) serão garantidas?

#### Fase 3 — Tarefas ("em que passos")

Decompõe o design em um plano de execução incremental e verificável.

- Lista de tarefas concretas, ordenadas por dependência
- Cada tarefa é pequena, rastreável a um requisito e tem critério de conclusão
- Permite acompanhar o progresso e entregar valor de forma incremental

---

### 3. Escrevendo Bons Requisitos

A fase de requisitos é a que mais previne falhas — e a mais negligenciada. Um bom requisito é **claro, verificável e rastreável**.

#### Estrutura de um requisito

Um formato amplamente usado associa uma história de usuário a critérios de aceitação:

```
História do usuário:
Como [papel], quero [funcionalidade], para que [benefício].

Critérios de aceitação:
1. QUANDO [evento] ENTÃO o sistema DEVE [resposta esperada]
2. SE [condição] ENTÃO o sistema DEVE [comportamento]
```

#### Exemplo aplicado a um projeto de dados

> **História:** Como gestor comercial, quero um indicador diário de inadimplência por região, para que eu possa redirecionar a equipe de cobrança antes do fechamento do mês.
>
> **Critérios de aceitação:**
> 1. QUANDO o painel for aberto ENTÃO o sistema DEVE exibir a inadimplência consolidada com, no máximo, 24 horas de defasagem.
> 2. SE uma região não tiver dados no dia ENTÃO o sistema DEVE sinalizar "dado indisponível" em vez de exibir zero.
> 3. QUANDO um valor divergir da fonte oficial ENTÃO o sistema DEVE permitir rastrear o dado até a origem (lineage).

#### Características de um bom requisito

| Característica | Pergunta de verificação |
|---------------|------------------------|
| **Claro** | Duas pessoas leem e entendem a mesma coisa? |
| **Verificável** | É possível testar objetivamente se foi atendido? |
| **Rastreável** | Está ligado a uma necessidade de negócio concreta? |
| **Viável** | Pode ser atendido com os dados e recursos disponíveis? |
| **Não ambíguo** | Evita termos vagos como "rápido", "amigável", "robusto"? |

#### Por que critérios de aceitação importam

Sem critérios de aceitação, "o relatório precisa ser rápido" pode significar 1 segundo para o analista e 1 hora para o engenheiro. O critério verificável ("deve carregar em menos de 3 segundos para 95% das consultas") elimina a ambiguidade e cria um contrato objetivo entre negócio e técnico.

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: Especificando um Projeto de Dados do Zero

Uma rede de farmácias com 400 lojas em todo o país percebeu que perde vendas por rupturas de estoque (produto em falta na prateleira) e, ao mesmo tempo, imobiliza capital com excesso de estoque de produtos de baixo giro. Hoje, cada gerente de loja faz pedidos de reposição com base na própria experiência e em uma planilha que consolida vendas da semana anterior.

A diretoria quer um projeto de dados que apoie decisões de reposição de estoque de forma centralizada e orientada por dados. Não há ainda nenhuma especificação — apenas o desejo da diretoria e um orçamento aprovado. O time de dados foi instruído a "não começar a construir nada antes de ter uma especificação clara".

As fontes de dados disponíveis incluem: histórico de vendas por loja e produto (sistema de PDV), posição atual de estoque por loja (ERP), calendário de datas comerciais e feriados, dados climáticos por região e histórico de rupturas registradas manualmente pelos gerentes.

### Questões para análise e discussão

**1. Fase de Requisitos (25 min)**
Escreva a especificação de requisitos do projeto:
- Qual é a pergunta de negócio central que o projeto deve responder?
- Escreva ao menos 2 requisitos no formato "História do usuário + critérios de aceitação", com critérios verificáveis.
- Quais são as restrições do projeto (prazo, qualidade mínima dos dados, LGPD, dependência de dados preenchidos manualmente)?

**2. Fase de Design (25 min)**
A partir dos requisitos escritos, esboce o design do projeto conectando com os conceitos das aulas anteriores:
- Qual arquitetura de dados é adequada (DW, Data Lake, Lakehouse) e por quê?
- Das fontes disponíveis, quais entrariam no MVP (use o framework de priorização da Aula 4)?
- Que problemas de qualidade (Aula 5) o grupo antecipa, considerando que algumas fontes são preenchidas manualmente?

**3. Transferência para o seu setor (20 min)**
Escolha uma iniciativa de dados real ou plausível no setor do grupo e produza o início de sua especificação:
- Escreva a pergunta de negócio e um requisito completo (história + critérios de aceitação).
- Qual seria a primeira tarefa concreta e verificável da fase de execução?
- Por que especificar antes teria evitado algum problema que o grupo já viu acontecer na prática?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca na questão: por que, mesmo sabendo que especificar antes reduz riscos, as organizações insistem em "começar a construir" sem especificação? Quais são as barreiras reais e como superá-las?

---

## Síntese do Curso

| Aula | Tema | Conceito central |
|------|------|-----------------|
| 1 | Big Data e seus desafios | Os 5 V's; OLTP vs. OLAP; limites das ferramentas tradicionais |
| 2 | Data Science como vantagem | Ciclo de vida analítico; os 4 tipos de análise |
| 3 | Arquiteturas de dados | DW × Data Lake × Lakehouse; Arquitetura Medallion |
| 4 | Construindo um Data Lake | Priorização de fontes; governança mínima; business case |
| 5 | Qualidade de dados | 6 dimensões; CODB; ciclo contínuo de Data Quality |
| 6 | Governança e LGPD | Papéis de governança; bases legais; Data Mesh |
| 7 | Spec-Driven para projetos de dados | Requisitos → Design → Tarefas; critérios de aceitação verificáveis |

---

## Leituras Complementares

- Wiegers, K. & Beatty, J. (2013). *Software Requirements* — Capítulos 1 e 2 (fundamentos de requisitos, aplicáveis a projetos de dados).
- Gartner. *How to Build a Winning Data and Analytics Strategy* (Executive Summary).
- DAMA International. *DAMA-DMBOK* — seção sobre planejamento e escopo de iniciativas de dados.

---

## Próxima Aula

➡️ [Aula 8 — Apresentação do Trabalho Final](../aula_08/)

**Lembrete:** Entrega do documento escrito no início da Aula 8. Consulte as instruções completas em [`aula_08/TRABALHO_FINAL.md`](../aula_08/TRABALHO_FINAL.md).
