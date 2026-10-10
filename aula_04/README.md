# Aula 4 — Construindo um Data Lake: Estratégia e Decisões de Negócio

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Aplicar um framework para priorizar fontes de dados em um projeto de Data Lake
2. Avaliar o trade-off entre valor de negócio e complexidade técnica na escolha de fontes
3. Identificar os elementos de governança mínima necessários antes de ingerir qualquer dado
4. Antecipar os principais riscos de implantação de um Data Lake e como mitigá-los
5. Construir um business case simplificado para uma iniciativa de dados

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Priorização de fontes | Framework valor × complexidade e tipologia de fontes | 45 min |
| Teoria — Governança mínima | Data Owner, classificação de sensibilidade, catálogo inicial | 35 min |
| Intervalo | — | 10 min |
| Teoria — Riscos e business case | Principais armadilhas e estrutura de justificativa | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: A estratégia de dados da Ambev | 70 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. Framework de Priorização de Fontes de Dados

Nem toda fonte de dados vale o mesmo esforço. Ao iniciar um projeto de Data Lake, a escolha do que ingerir primeiro determina se o projeto entregará valor rápido ou desperdiçará meses em integrações complexas de baixo retorno.

#### Matriz Valor × Complexidade

Para cada fonte candidata, avalie dois eixos:

**Valor de negócio** — responde a decisões do C-Suite? Reduz custo ou aumenta receita diretamente? Existe demanda reprimida clara dos usuários?

**Complexidade de integração** — dado não estruturado? Sistema legado sem documentação? Dado sensível sujeito à LGPD? Proprietário externo difícil de acionar?

| Quadrante | Valor | Complexidade | Estratégia |
|-----------|-------|--------------|------------|
| **Quick Wins** | Alto | Baixa | Comece aqui — entregue valor em 90 dias |
| **Estratégicos** | Alto | Alta | Planeje com cuidado; projeto formal com cronograma realista |
| **Baixa prioridade** | Baixo | Baixa | Desconsidere por ora |
| **Evitar agora** | Baixo | Alta | Muito esforço, pouco retorno; risco de desviar o foco |

**Regra de ouro do MVP:** foque nos Quick Wins. Eles entregam resultado visível em 90 dias e provam o conceito para o board.

#### Tipologia de fontes de dados

| Tipo | Exemplos | Complexidade típica |
|------|----------|---------------------|
| Internas estruturadas | ERP, CRM, sistemas transacionais | Média |
| Internas semi-estruturadas | Logs de sistema, formulários web, e-mails | Alta |
| Internas não estruturadas | Documentos, PDFs, imagens, áudios | Muito alta |
| Externas públicas | IBGE, Banco Central, órgãos reguladores | Baixa |
| Externas comerciais | Dados de mercado, enriquecimento cadastral | Média |
| Streaming / IoT | Sensores, wearables, clickstream | Alta |

---

### 2. Governança Mínima — O que Definir Antes do Primeiro Byte

Projetos que começam a ingerir dados sem governança mínima invariavelmente criam Data Swamps. Quatro elementos são inegociáveis antes de iniciar:

#### 1. Data Owner

Para cada fonte de dados, defina quem é responsável pela:
- Precisão e atualização do dado
- Autorização de acesso
- Definição do que o dado significa (semântica)

Sem dono, o dado não tem responsável quando algo dá errado — e algo sempre dá errado.

#### 2. Classificação de sensibilidade

| Nível | Descrição | Controle de acesso |
|-------|-----------|-------------------|
| Público | Pode ser compartilhado externamente | Sem restrição |
| Interno | Uso interno geral | Colaboradores autenticados |
| Confidencial | Restrição por área ou função | Need-to-know |
| Sensível / LGPD | Dados pessoais, dados de saúde | Controles especiais, anonimização obrigatória |

#### 3. SLA de qualidade mínimo

Para cada fonte, defina:
- Frequência de atualização esperada
- Completude mínima aceitável (ex.: campo CPF preenchido em 99% dos registros)
- O que acontece quando o dado não chega no prazo

#### 4. Catálogo de dados inicial

Para cada fonte ingerida, documente no mínimo: nome, descrição, sistema de origem, Data Owner, frequência de atualização, nível de sensibilidade e dicionário de variáveis principais.

---

### 3. Principais Riscos e Business Case

#### Riscos que mais matam projetos de Data Lake

| Risco | Probabilidade | Como mitigar |
|-------|--------------|--------------|
| Data Swamp (dado sem dono e sem qualidade) | Alta | Governança mínima antes de ingerir qualquer fonte |
| Escopo infinito | Alta | MVP com 3–5 fontes; entrega em 90 dias |
| Falta de casos de uso definidos | Alta | Definir 2–3 perguntas de negócio antes de construir a infraestrutura |
| Resistência dos sistemas legados | Média | Envolver os donos dos sistemas desde o início |
| Violação de LGPD | Média | Classificação de sensibilidade obrigatória antes do primeiro acesso |
| Custo fora de controle | Média | Monitoramento de custo de armazenamento desde o início |

#### Estrutura de business case

| Elemento | O que incluir |
|----------|---------------|
| Problema atual | Qual decisão importante está sendo tomada com dados ruins ou atrasados? |
| Top 3 fontes (MVP) | Quais fontes priorizar pelo framework valor × complexidade? |
| Caso de uso principal | Qual análise será possível com essas 3 fontes nos primeiros 90 dias? |
| Benefício quantificável | Redução de custo, aumento de receita, ou melhoria de NPS estimada |
| Investimento estimado | Pessoas + tecnologia + tempo (ordem de magnitude) |
| ROI esperado | Benefício / Investimento em 12 meses |
| Risco principal | Maior ameaça ao projeto e plano de mitigação |

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: A Estratégia de Dados da Ambev

A Ambev, maior cervejaria da América Latina, iniciou sua transformação data-driven em larga escala por volta de 2017–2018. O desafio central era conectar dados de uma cadeia extremamente complexa: produção industrial em 30 fábricas, distribuição por mais de 100 centros de distribuição, vendas para mais de 1 milhão de pontos de venda (bares, restaurantes, mercados) em todo o Brasil, e consumidores finais cada vez mais conectados.

Antes da transformação, cada elo da cadeia operava com sistemas e relatórios independentes. O time comercial não sabia o que o time de distribuição sabia; a produção não tinha visibilidade da demanda em tempo real; e os gestores regionais recebiam relatórios mensais consolidados com dados de semanas atrás.

A Ambev investiu em uma plataforma de dados unificada que ingestiona dados de múltiplas fontes: sistemas de ponto de venda (POS) de parceiros, dados de campo dos representantes (via app), dados de produção das fábricas, dados climáticos (temperatura afeta diretamente o consumo de cerveja), dados de redes sociais e, mais recentemente, dados de IoT de geladeiras conectadas instaladas em pontos de venda.

Com essa plataforma, a empresa conseguiu: reduzir o nível de estoque dos distribuidores em 15% sem aumentar rupturas; identificar oportunidades de mercado não atendidas por região; e personalizar a oferta de produtos por canal e por perfil de ponto de venda.

### Questões para análise e discussão

**1. Priorização de fontes (20 min)**
Das fontes mencionadas no caso (POS, dados de campo, dados de produção, dados climáticos, redes sociais, IoT de geladeiras), classifique cada uma na matriz Valor × Complexidade. Quais 3 fontes você escolheria para o MVP? Justifique usando os critérios do framework.

**2. Governança e riscos (25 min)**
Para as 3 fontes escolhidas no MVP:
- Quem seria o Data Owner de cada fonte dentro da Ambev?
- Qual seria o nível de sensibilidade de cada fonte (considerando LGPD)?
- Quais são os 2 maiores riscos do projeto de Data Lake da Ambev e como você os mitigaria?

**3. Transferência para o seu setor (25 min)**
Construa um business case simplificado para uma iniciativa de Data Lake em uma organização do setor do grupo:
- Qual é o problema atual (decisão tomada com dados ruins ou atrasados)?
- Quais 3 fontes compõem o MVP?
- Qual é o caso de uso principal nos primeiros 90 dias?
- Qual é o benefício quantificável esperado?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca na questão: qual é a diferença entre um business case de Data Lake bem construído e um que apenas justifica uma decisão já tomada?

---

## Leituras Complementares

- Gartner. *How to Build a Winning Data and Analytics Strategy* (Executive Summary)
- McKinsey & Company. *Designing data governance that delivers value* [mckinsey.com]
- Harvard Business Review. *The New Decision Makers: Equipping Frontline Workers for Data-Driven Action* (2020)

---

## Próxima Aula

➡️ [Aula 5 — Qualidade e Confiabilidade dos Dados](../aula_05/)
