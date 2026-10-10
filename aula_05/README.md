# Aula 5 — Qualidade e Confiabilidade dos Dados

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Explicar por que a qualidade dos dados é um problema de negócio, não apenas técnico
2. Identificar e aplicar as 6 dimensões de qualidade de dados a situações reais
3. Calcular e estimar o custo da má qualidade de dados (CODB) de forma simplificada
4. Descrever o funcionamento de um processo de Data Quality como ciclo contínuo
5. Compreender o papel do catálogo de dados e do data lineage na rastreabilidade e confiança

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — As 6 dimensões de qualidade | Definições, exemplos e consequências de negócio | 40 min |
| Teoria — Custo da má qualidade | CODB: como estimar e comunicar o impacto financeiro | 30 min |
| Intervalo | — | 10 min |
| Teoria — Data Quality como processo | Ciclo contínuo, papéis e responsabilidades | 30 min |
| Teoria — Catálogo de dados e lineage | Rastreabilidade como base de confiança | 20 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: Qualidade de dados na saúde pública brasileira | 70 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. As 6 Dimensões de Qualidade de Dados

Qualidade de dados não é uma propriedade binária (bom/ruim). É multidimensional — e cada dimensão tem impacto de negócio diferente.

| Dimensão | Definição | Exemplo de problema | Consequência de negócio |
|----------|-----------|---------------------|------------------------|
| **Completude** | Todo campo obrigatório está preenchido? | 23% dos registros de clientes sem estado cadastrado | Relatório regional distorcido; modelo treinado com viés geográfico |
| **Consistência** | Os dados concordam entre si em diferentes sistemas? | CPF do cliente diferente no CRM e no ERP | Cobrança enviada para destinatário errado; falha na reconciliação financeira |
| **Precisão** | O dado reflete a realidade corretamente? | Data de nascimento "01/01/1900" para cliente adulto | Modelo de risco viciado; análise de perfil demográfico incorreta |
| **Oportunidade** | O dado está disponível quando é necessário? | Resultado de venda disponível 45 dias após o fechamento | Análise de tendência sempre defasada; reação tardia a variações de mercado |
| **Unicidade** | Não há duplicatas indesejadas? | Mesmo cliente com dois cadastros ativos | Contagem de clientes inflada; campanha enviada em duplicidade |
| **Validade** | O dado respeita formatos e regras definidas? | CEP com 7 dígitos; CNPJ com dígito verificador inválido | Integração com sistema externo falha; relatório regulatório rejeitado |

#### Interação entre dimensões

As dimensões não são independentes: um problema de completude em um sistema pode causar inconsistência ao ser integrado com outro. Um problema de validade pode passar despercebido e comprometer a precisão de análises futuras.

---

### 2. Custo da Má Qualidade de Dados (CODB)

Pesquisas da IBM e Gartner estimam que má qualidade de dados custa às organizações entre 15% e 25% de sua receita operacional — na maioria dos casos, sem que os gestores percebam.

#### Tipos de custo

**Custos diretos:**
- Retrabalho: horas gastas por analistas corrigindo dados manualmente
- Erros operacionais: cobranças erradas, pedidos cancelados, reprocessamentos
- Multas regulatórias: ANPD (LGPD), ANS, Bacen, CVM — cada setor tem seu regulador

**Custos indiretos:**
- Decisões erradas tomadas com dados incorretos (custo muitas vezes invisível, mas real)
- Perda de confiança dos usuários nos relatórios — paralisa a cultura data-driven
- Oportunidades perdidas: análise adiada indefinidamente por falta de qualidade nos dados

#### Cálculo simplificado do CODB

```
CODB = (Horas de retrabalho/semana × custo médio/hora × 52)
     + (Taxa de erro × Volume de operações × Custo médio por erro)
     + (Risco de multa regulatória × Probabilidade estimada)
```

**Sinal de alerta:** Se a resposta à pergunta *"você confia nos seus dados?"* for *"depende de qual relatório"*, o CODB da organização é alto — e está sendo pago silenciosamente toda semana.

---

### 3. Data Quality como Processo Contínuo

Qualidade de dados não é um projeto com início, meio e fim. É uma prática operacional permanente — como controle de qualidade na indústria.

#### O ciclo de Data Quality

```
1. DEFINIR       → Quais são as regras de qualidade para cada dado?
2. MEDIR         → Qual é o estado atual? (baseline)
3. MONITORAR     → Alertar quando a qualidade cair abaixo do limiar definido
4. CORRIGIR      → Resolver os problemas identificados
5. PREVENIR      → Atacar a causa raiz na fonte (não apenas os sintomas)
    └── Volta para 1 (ciclo contínuo)
```

#### Divisão de responsabilidades

| Responsabilidade | Negócio | Técnico |
|----------------|---------|---------|
| Definir regras de qualidade | ✅ Protagonista | Suporte |
| Implementar validações automatizadas | Suporte | ✅ Protagonista |
| Aprovar o critério de "dado limpo" | ✅ Protagonista | Suporte |
| Monitorar indicadores de qualidade | ✅ Protagonista | ✅ Protagonista |
| Investigar anomalias | ✅ Protagonista | Suporte |
| Corrigir na fonte (no sistema de origem) | ✅ Protagonista | Suporte |

A área de negócio define o que é qualidade; TI implementa os controles. Quando a TI define as regras sozinha, elas ficam tecnicamente corretas mas semanticamente erradas.

---

### 4. Catálogo de Dados e Data Lineage

#### Catálogo de dados

O catálogo de dados é o inventário gerenciado de todos os ativos de dados de uma organização. Funciona como um "Google interno dos dados":

- Permite buscar: *"quais datasets têm informações sobre inadimplência de clientes?"*
- Responde: o que este campo significa? Quem é o dono? Quando foi atualizado?
- Registra quem acessa quais dados e com qual finalidade (essencial para LGPD)

#### Data Lineage

Lineage é a rastreabilidade do caminho percorrido por um dado — da fonte até o relatório final.

- Responde: *"De onde vem exatamente o número X que está neste relatório?"*
- Quando um número está errado, permite rastrear a causa até a fonte sem investigação manual
- Essencial para auditorias regulatórias e para reconstruir a confiança após um incidente de qualidade

**Metáfora:** O catálogo é o cardápio de um restaurante com lista de ingredientes. O lineage é a rastreabilidade da fazenda de origem de cada ingrediente. Juntos, constroem confiança no que está sendo consumido.

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: Qualidade de Dados no SUS — O DATASUS e os Limites da Análise em Saúde Pública

O DATASUS é o principal sistema de informações em saúde do Brasil, mantido pelo Ministério da Saúde. Concentra dados de produção ambulatorial, internações hospitalares, procedimentos cirúrgicos, mortalidade e nascimentos de todo o sistema público de saúde. Pesquisadores, gestores municipais, secretarias estaduais e o próprio Ministério usam esses dados para tomar decisões sobre políticas públicas, alocação de recursos e vigilância epidemiológica.

Estudos acadêmicos publicados no Brasil e no exterior documentam problemas recorrentes de qualidade nos dados do DATASUS:

- **Incompletude:** campos de escolaridade, raça/cor e ocupação do paciente apresentam taxas de preenchimento inferiores a 60% em diversas bases, o que limita análises de equidade em saúde
- **Inconsistência:** a causa básica de óbito (CID-10) registrada nas declarações de óbito frequentemente diverge do registro nos sistemas hospitalares, dificultando a análise de mortalidade por causa
- **Defasagem:** o processamento e disponibilização dos dados pode levar de 2 a 18 meses após o evento, tornando o sistema inadequado para vigilância em tempo real
- **Subnotificação:** municípios menores e regiões com infraestrutura limitada apresentam taxas de notificação sistematicamente menores, criando viés geográfico nas análises nacionais

Durante a pandemia de COVID-19 (2020–2022), esses problemas se tornaram críticos: decisões sobre lockdowns, distribuição de leitos de UTI e compra de insumos eram tomadas com dados fragmentados, defasados e, em alguns casos, deliberadamente manipulados por gestores locais para mascarar a situação real.

### Questões para análise e discussão

**1. Diagnóstico de qualidade (20 min)**
Com base nas dimensões de qualidade estudadas, classifique cada problema descrito no caso (incompletude, inconsistência, defasagem, subnotificação) na dimensão correspondente. Para cada um, descreva:
- Qual decisão de políticas públicas é comprometida por esse problema?
- Qual seria o custo estimado (social, econômico ou humano) desse problema de qualidade?

**2. Responsabilidades e ciclo de DQ (25 min)**
O DATASUS envolve múltiplas camadas: hospitais e postos de saúde (produtores dos dados), municípios, estados e Ministério da Saúde (integradores). Aplique o ciclo de Data Quality a esse contexto:
- Quem deveria ser o "Data Owner" de cada tipo de dado (internações, mortalidade, procedimentos)?
- Como um processo de monitoramento contínuo funcionaria nesse contexto federado?
- Qual mudança no processo de geração do dado (no sistema de origem — hospitais e postos) teria maior impacto na qualidade?

**3. Transferência para o seu setor (25 min)**
Todo setor tem seus "DATASUS" — sistemas críticos com problemas crônicos de qualidade que todos conhecem mas poucos endereçam sistematicamente. Identifique um sistema de dados do setor do grupo com problemas de qualidade conhecidos:
- Quais dimensões de qualidade estão comprometidas?
- Qual decisão importante está sendo tomada com esses dados de qualidade duvidosa?
- Qual seria uma intervenção de alto impacto para melhorar a qualidade — na fonte (quem gera) ou no processamento (quem integra)?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca na questão: por que organizações continuam tomando decisões com dados que sabem ser de qualidade duvidosa? Quais são as barreiras reais para melhorar a qualidade de dados?

---

## Leituras Complementares

- DAMA International. *DAMA-DMBOK: Data Management Body of Knowledge* — Capítulo 13: Data Quality.
- Redman, T.C. (2016). *Getting in Front on Data: Who Does What*. Technics Publications.
- IBM Institute for Business Value. *The real cost of poor data quality* [ibm.com/downloads].

---

## Próxima Aula

➡️ [Aula 6 — Governança, Privacidade e LGPD](../aula_06/)
