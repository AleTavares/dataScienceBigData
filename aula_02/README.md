# Aula 2 — Data Science como Vantagem Competitiva

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Explicar o ciclo de vida de um projeto de Data Science do ponto de vista executivo
2. Diferenciar os quatro tipos de análise (descritiva, diagnóstica, preditiva, prescritiva) e associar cada um a decisões de negócio
3. Avaliar quando vale investir em análise preditiva versus descritiva
4. Estruturar o business case de uma iniciativa de dados
5. Questionar resultados de modelos com as perguntas corretas, sem precisar entender os algoritmos

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Ciclo de vida analítico | Da pergunta ao insight: as etapas de um projeto de Data Science | 40 min |
| Teoria — Os 4 tipos de análise | A escada de valor analítico: descritivo → prescritivo | 40 min |
| Intervalo | — | 10 min |
| Teoria — Business case e perguntas ao modelo | Como justificar investimentos e avaliar resultados | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: Como o Nubank usa Data Science | 70 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. Ciclo de Vida de um Projeto de Data Science

A maioria dos projetos de dados falha não por problemas técnicos, mas por ausência de estrutura no processo. O ciclo de vida analítico organiza as etapas e as responsabilidades:

```
1. DEFINIÇÃO DO PROBLEMA
   "Qual pergunta de negócio queremos responder?"
   Responsável: negócio (não a equipe técnica)

2. COLETA E INTEGRAÇÃO DOS DADOS
   "Quais fontes temos? O que está faltando?"

3. EXPLORAÇÃO E QUALIDADE
   "Os dados são confiáveis? O que eles revelam?"
   ⚠️ Consome 60–80% do tempo real de qualquer projeto

4. MODELAGEM E ANÁLISE
   "Que padrões podemos extrair? Que previsões podemos fazer?"

5. VALIDAÇÃO
   "O modelo funciona fora dos dados de treinamento? Com que confiança podemos confiar?"

6. COMUNICAÇÃO E AÇÃO
   "Como transformar o insight em decisão e resultado?"

7. MONITORAMENTO CONTÍNUO
   "O modelo continua preciso? O comportamento dos dados mudou?"
```

#### Onde gestores erram mais

| Erro | O que acontece | Como evitar |
|------|---------------|-------------|
| Pular a etapa 1 | Projeto tecnicamente correto, sem impacto no negócio | Exigir pergunta de negócio clara antes de qualquer aprovação |
| Subestimar etapas 2 e 3 | Cronograma explode; meses gastos limpando dados | Multiplicar por 3 qualquer estimativa de prazo de preparação de dados |
| Cobrar etapa 4 sem qualidade na 3 | "Garbage in, garbage out" — modelo inútil ou enganoso | Não há atalho: dados ruins geram conclusões ruins |
| Esquecer etapa 7 | Modelo decai silenciosamente; decisões pioram sem que ninguém perceba | Incluir monitoramento contínuo no escopo e no orçamento desde o início |

---

### 2. Os 4 Tipos de Análise — A Escada de Valor

| Nível | Tipo | Pergunta respondida | Complexidade | Valor gerado |
|-------|------|---------------------|--------------|--------------|
| 1 | **Descritiva** | O que aconteceu? | Baixa | Entendimento do passado |
| 2 | **Diagnóstica** | Por que aconteceu? | Média | Causa identificada |
| 3 | **Preditiva** | O que vai acontecer? | Alta | Antecipação |
| 4 | **Prescritiva** | O que devemos fazer? | Muito alta | Otimização de decisão |

**Regra prática:** A maioria das organizações brasileiras ainda está entre os níveis 1 e 2. Chegar ao nível 2 já representa salto enorme. O nível 4 exige que os três anteriores estejam consolidados.

#### Onde cada tipo aparece no mundo real

| Setor | Descritiva | Diagnóstica | Preditiva | Prescritiva |
|-------|-----------|-------------|-----------|-------------|
| Saúde | Perfil de sinistros por região | Por que o custo de internações subiu? | Quais pacientes têm risco de reinternação? | Qual protocolo preventivo maximiza saúde e minimiza custo? |
| Varejo | Ticket médio por canal | Por que a conversão caiu no app? | Qual cliente tem propensão de churn? | Qual oferta enviar para cada cliente no momento certo? |
| Financeiro | Volume de transações por produto | Por que houve aumento de inadimplência? | Qual é o score de crédito deste cliente? | Qual limite de crédito otimiza rentabilidade e risco? |
| Logística | Tempo médio de entrega por rota | Por que essa rota tem mais atrasos? | Qual será a demanda por essa rota na próxima semana? | Como realocar frota para minimizar custo e prazo? |

---

### 3. Business Case e Perguntas ao Modelo

#### Estrutura de um business case para uma iniciativa de dados

| Elemento | O que incluir |
|----------|---------------|
| **Problema de negócio** | Qual decisão específica será melhorada? (não "queremos ser data-driven") |
| **Tipo de análise** | Descritiva / diagnóstica / preditiva / prescritiva? |
| **Pergunta analítica** | Reformule o problema como pergunta mensurável |
| **Dados disponíveis** | Quais fontes já existem? |
| **Dados faltantes** | O que precisará ser coletado ou adquirido? |
| **Métrica de sucesso** | Como saberemos que o projeto foi bem-sucedido? |
| **Impacto estimado** | Redução de custo, aumento de receita ou melhoria de NPS? |
| **Risco principal** | O que pode fazer o projeto falhar? |

#### 6 perguntas que todo gestor deve fazer ao receber um modelo

1. **"Qual pergunta exata você respondeu?"** — Evita modelos tecnicamente corretos mas sem propósito de negócio.
2. **"Com que dados você treinou?"** — Dados históricos refletem o passado; o futuro pode ter padrões diferentes.
3. **"Qual é a taxa de erro e o que acontece quando o modelo erra?"** — Todo modelo erra; o custo do erro neste contexto precisa ser explícito.
4. **"O modelo foi validado fora dos dados de treinamento?"** — Teste essencial para evitar overfitting.
5. **"Há viés nos dados?"** — Um modelo de risco de saúde treinado só com pacientes que chegaram ao hospital ignora os que não chegaram.
6. **"Com que frequência o modelo é reavaliado?"** — Comportamentos mudam; modelos que não são monitorados envelhecem silenciosamente.

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: Nubank e o Score de Crédito Próprio

O Nubank foi fundado em 2013 sem acesso a histórico de relacionamento bancário dos clientes — seu público-alvo eram justamente as pessoas sem conta em banco ou com histórico limitado. O desafio: como avaliar o risco de crédito de quem os bureaus tradicionais classificavam como "sem score"?

A empresa desenvolveu modelos preditivos próprios usando fontes de dados não convencionais: comportamento no app (quantas vezes o usuário abre o aplicativo, em que horários, com que frequência consulta o saldo), padrões de uso do cartão, dados de geolocalização anonimizados, comportamento em redes sociais (com consentimento) e dados alternativos como estabilidade de endereço e frequência de compras em estabelecimentos fixos.

Com isso, o Nubank conseguiu oferecer crédito a perfis que bancos tradicionais rejeitavam — e com taxa de inadimplência inferior à média do setor. Em 2023, o banco reportou que mais de 40% dos seus clientes de crédito não teriam aprovação em um banco tradicional com os critérios convencionais.

### Questões para análise e discussão

**1. Tipo de análise envolvida (15 min)**
O modelo de score de crédito do Nubank pertence a qual nível da escada analítica? Justifique. Que tipos de análise (descritiva, diagnóstica) foram necessários antes de chegar a esse nível?

**2. Ciclo de vida do projeto (25 min)**
Reconstrua, do ponto de vista executivo, como seria o ciclo de vida do projeto de score de crédito do Nubank:
- Qual foi a pergunta de negócio original?
- Quais fontes de dados não convencionais o grupo imagina que foram usadas?
- Qual seria a métrica de sucesso do modelo (não uma métrica técnica — uma de negócio)?
- Quais riscos de viés o grupo identifica no uso desses dados alternativos?

**3. Transferência para o seu setor (30 min)**
Existe no setor de atuação do grupo algum problema em que o "cliente invisível" — alguém que os sistemas atuais não conseguem avaliar bem — representa uma oportunidade?
- Descreva o problema.
- Que dados alternativos (não convencionais) poderiam ajudar a resolvê-lo?
- Qual seria o tipo de análise necessário?
- Quais riscos éticos ou de privacidade esse uso de dados levanta?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca nos riscos éticos identificados — o professor facilita a discussão sobre onde está a linha entre inovação analítica e uso indevido de dados.

---

## Leituras Complementares

- Davenport, T.H. (2014). *What do you really mean by Business Analytics?* Harvard Business Review.
- Provost, F. & Fawcett, T. (2013). *Data Science for Business* — Capítulo 1.
- O'Neil, C. (2016). *Weapons of Math Destruction* — Capítulo 1 (viés em modelos preditivos).

---

## Próxima Aula

➡️ [Aula 3 — Arquiteturas de Dados](../aula_03/)
