# Aula 1 — O que é Big Data e por que isso muda tudo

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Definir Big Data e os 5 V's com exemplos do seu setor
2. Diferenciar dados transacionais de dados analíticos (OLTP vs. OLAP)
3. Explicar por que ferramentas tradicionais (Excel, bancos relacionais) não escalam para análise em larga escala
4. Relacionar Big Data a decisões de negócio mais rápidas e mais precisas

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Big Data e os 5 V's | Conceito, definição e dimensões do Big Data | 40 min |
| Teoria — OLTP vs. OLAP | Dados transacionais vs. analíticos; limites das ferramentas tradicionais | 40 min |
| Intervalo | — | 10 min |
| Teoria — Big Data como vantagem competitiva | Setores e tipos de decisão transformados por dados | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: Como o iFood usa Big Data | 70 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. O que é Big Data

**Definição:** Conjuntos de dados cujo volume, velocidade ou variedade excedem a capacidade das ferramentas tradicionais de coletar, armazenar, processar e analisar.

> Big Data não é apenas sobre tamanho — é sobre a combinação de desafios que surgem quando os dados crescem além do que as ferramentas convencionais suportam.

#### Os 5 V's do Big Data

| V | Definição | Exemplos práticos |
|---|-----------|-------------------|
| **Volume** | Quantidade massiva de dados gerada continuamente | Bilhões de transações diárias; históricos de décadas em operadoras de saúde |
| **Velocidade** | Taxa de geração e necessidade de processamento em tempo real | Autorizações médicas em &lt; 3s; detecção de fraude em &lt; 100ms |
| **Variedade** | Múltiplos formatos: estruturado, semi-estruturado e não estruturado | Tabelas SQL + PDFs + áudios + imagens de satélite + logs de sistema |
| **Veracidade** | Qualidade e confiabilidade dos dados | Dados duplicados, CIDs inválidos, campos nulos, registros desatualizados |
| **Valor** | Capacidade de transformar dados em decisões e receita | Previsão de demanda, personalização, redução de custo operacional |

Os 5 V's não são desafios independentes: mais Volume tende a ampliar problemas de Veracidade e Velocidade.

---

### 2. Dados Transacionais vs. Analíticos

#### OLTP — Online Transaction Processing
- Projetado para **registrar operações** do dia a dia com rapidez
- Otimizado para inserções e atualizações de registros individuais
- Péssimo para consultas que varrem milhões de registros históricos
- Exemplos: ERP, sistema hospitalar, plataforma de e-commerce

#### OLAP — Online Analytical Processing
- Projetado para **analisar padrões** sobre grandes volumes históricos
- Otimizado para leituras agregadas (SUM, AVG, COUNT por dimensões)
- Exemplos: Data Warehouse, Data Lake, ferramentas de BI

| Característica | OLTP | OLAP |
|----------------|------|------|
| Objetivo | Registrar operações | Analisar padrões |
| Volume por consulta | Poucos registros | Milhões de registros |
| Frequência de atualização | Tempo real | Batch / streaming |
| Usuário típico | Operador, atendente | Analista, gestor, executivo |
| Ferramenta típica | ERP, CRM | DW, Data Lake, BI |

#### Por que planilhas não escalam

| Limitação | Impacto |
|-----------|---------|
| Limite de ~1M de linhas | Uma fintech gera isso por hora |
| Colaboração sequencial | Múltiplas versões divergentes do mesmo arquivo |
| Sem rastreabilidade | Impossível auditar quem mudou o quê |
| Análise manual | Cada cruzamento exige trabalho humano repetível |
| Snapshot estático | Decisão baseada em passado defasado |

**Caso documentado:** Em 2020, o Reino Unido não reportou ~16.000 casos de COVID-19 porque o arquivo Excel antigo (formato .XLS) atingiu o limite de colunas. Dados corretos existiam — a ferramenta não comportou.

---

### 3. Big Data como Vantagem Competitiva

#### Antes e depois das decisões baseadas em dados

| Decisão | Antes (intuição/experiência) | Depois (dados) |
|---------|------------------------------|----------------|
| Onde abrir uma nova loja | Feeling do gestor regional | Cruzamento de renda, concorrência, fluxo, geodados |
| Precificação de seguro | Tabelas históricas fixas | Score individualizado em tempo real |
| Estoque de medicamentos | Pedido mensal baseado no mês anterior | Previsão de demanda por sazonalidade, epidemias, perfil da região |
| Detecção de fraude | Revisão manual pós-ocorrência | Modelo em tempo real com 99,8% de precisão |

#### Casos de uso por setor

| Setor | Decisão transformada por Big Data |
|-------|-----------------------------------|
| Saúde | Predição de risco de reinternação, detecção de fraude em sinistros, personalização de protocolo |
| Varejo | Precificação dinâmica, previsão de demanda, recomendação personalizada |
| Financeiro | Score de crédito em tempo real, detecção de fraude, otimização de portfólio |
| Logística | Roteamento dinâmico, previsão de falha em equipamentos, otimização de malha |
| Governo | Cruzamento de benefícios, alerta epidemiológico, previsão de inadimplência fiscal |

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: iFood e a Plataforma de Dados em Tempo Real

O iFood processa mais de **60 milhões de pedidos por mês** no Brasil. Para operar nessa escala, a empresa construiu uma plataforma de dados que processa eventos em tempo real: cliques, buscas, posição de entregadores, tempo de preparo dos restaurantes e avaliações pós-entrega.

Com esses dados, o iFood toma decisões em frações de segundo:
- Estimativa de tempo de entrega atualizada a cada 30 segundos
- Sugestão de restaurante personalizada por usuário, hora do dia e clima
- Identificação de entregadores com padrão de comportamento fraudulento
- Redistribuição dinâmica de entregadores por bairro conforme demanda em tempo real

Em 2022, o iFood anunciou que seu modelo de precificação dinâmica de fretes — baseado em dados de oferta e demanda em tempo real — reduziu o tempo médio de espera em 18% e aumentou a taxa de aceitação de pedidos por entregadores em 22%.

### Questões para análise e discussão

**1. Identificação dos 5 V's (20 min)**
Com base na descrição acima, identifique como cada um dos 5 V's se manifesta na operação do iFood. Para cada V, descreva:
- Como ele aparece na operação
- Qual seria a consequência se esse V não fosse endereçado

**2. OLTP vs. OLAP na prática (20 min)**
O sistema do iFood precisa de dois tipos de ambiente de dados ao mesmo tempo:
- Qual parte da operação exige OLTP? Por quê?
- Qual parte exige OLAP? Por quê?
- O que aconteceria se a empresa tentasse usar apenas um tipo de ambiente?

**3. Transferência para o seu setor (30 min)**
Escolha o setor de atuação predominante do grupo e responda:
- Que decisão no seu setor ainda é tomada sem dados (ou com dados defasados) que poderia se beneficiar de um modelo similar ao do iFood?
- Quais dos 5 V's seriam os mais desafiadores nesse contexto?
- Qual seria o impacto mensurável (em tempo, custo ou receita) de resolver esse problema com dados?

### Apresentação e debate
Cada grupo apresenta sua resposta à questão 3 (5 minutos por grupo). O professor facilita o debate comparando as abordagens entre setores diferentes.

---

## Leituras Complementares

- Davenport, T.H. & Patil, D.J. (2012). *Data Scientist: The Sexiest Job of the 21st Century*. Harvard Business Review.
- McAfee, A. & Brynjolfsson, E. (2012). *Big Data: The Management Revolution*. Harvard Business Review.
- DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge* — Capítulo 1: Introdução.

---

## Próxima Aula

➡️ [Aula 2 — Data Science como Vantagem Competitiva](../aula_02/)
