# Aula 3 — Arquiteturas de Dados: do Data Warehouse ao Data Lake

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Descrever a evolução histórica das arquiteturas de armazenamento de dados analíticos
2. Diferenciar Data Warehouse, Data Lake e Data Lakehouse com critérios objetivos
3. Explicar a Arquitetura Medallion (Bronze → Silver → Gold) e aplicá-la a exemplos concretos
4. Avaliar qual arquitetura é adequada para diferentes contextos organizacionais
5. Identificar os 4 componentes de um ambiente de Big Data (ingestão, armazenamento, processamento, consumo)

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Evolução das arquiteturas | OLTP → Data Warehouse → Data Lake → Lakehouse | 45 min |
| Teoria — Arquitetura Medallion | Bronze, Silver e Gold: a jornada de refinamento | 35 min |
| Intervalo | — | 10 min |
| Teoria — Componentes de um ambiente Big Data | Ingestão, armazenamento, processamento, consumo | 30 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: Arquitetura de dados do Mercado Livre | 70 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. Evolução das Arquiteturas de Dados

#### Era 1 — Banco de Dados Transacional (OLTP) — Anos 1970–1990

Projetado para registrar operações com rapidez e consistência. Péssimo para análise histórica de grandes volumes. Quando empresas tentavam fazer análise diretamente no banco transacional, travam o sistema operacional.

#### Era 2 — Data Warehouse — Anos 1990–2010

Surgiu para separar o ambiente analítico do transacional.

- Esquema rígido definido antes de armazenar os dados (*schema-on-write*)
- Dados estruturados, limpos e integrados
- Excelente para relatórios padronizados e dashboards de BI
- **Limitações:** não aceita dados não estruturados (textos, imagens, áudios); custo de armazenamento alto; baixa flexibilidade quando as perguntas de negócio mudam

#### Era 3 — Data Lake — Anos 2010–2020

Nasceu para endereçar as limitações do Data Warehouse.

- Armazena todos os dados no formato original, sem transformação prévia
- Esquema definido no momento da leitura (*schema-on-read*)
- Aceita qualquer tipo de dado: estruturado, semi-estruturado e não estruturado
- Custo de armazenamento muito menor (cloud storage)
- **A armadilha:** sem governança, o Data Lake vira um *Data Swamp* — dados acumulados que ninguém confia e ninguém usa

#### Era 4 — Data Lakehouse — Anos 2020–presente

Combina a flexibilidade do Data Lake com a confiabilidade do Data Warehouse.

- Adiciona camadas de transação, versionamento e controle de qualidade ao Data Lake
- Tecnologias principais: Delta Lake (Databricks), Apache Iceberg, Apache Hudi
- Permite SQL, ML e streaming sobre o mesmo repositório de dados

#### Comparativo

| Característica | Data Warehouse | Data Lake | Lakehouse |
|---------------|---------------|-----------|-----------|
| Tipos de dado suportados | Só estruturado | Qualquer tipo | Qualquer tipo |
| Esquema | Definido antes | Definido ao ler | Flexível com controle |
| Qualidade dos dados | Alta (por construção) | Variável | Alta (por processo) |
| Custo de armazenamento | Alto | Baixo | Baixo |
| Flexibilidade analítica | Baixa | Alta | Alta |
| Quando usar | Relatórios fixos, BI consolidado | Exploração, ML, dados brutos | Ambos os casos |

---

### 2. Arquitetura Medallion

A Arquitetura Medallion organiza os dados em três camadas progressivas de refinamento. O dado entra bruto e é refinado até estar pronto para consumo analítico.

```
FONTES                  BRONZE              SILVER              GOLD
──────                  ──────              ──────              ────
ERP                     Dados brutos        Dados limpos        KPIs prontos
CRM          ─────►     sem alteração  ─►   validados      ─►   para dashboards
APIs                    (imutável)          padronizados        e modelos
Arquivos                                    enriquecidos
```

| Camada | O que contém | Responsável | Analogia |
|--------|-------------|-------------|---------|
| **Bronze** | Dados brutos, exatamente como chegaram da fonte | Engenharia de dados | Minério bruto |
| **Silver** | Dados limpos, validados, sem duplicatas, padronizados | Engenharia + Analistas | Metal refinado |
| **Gold** | Indicadores agregados, modelos prontos, dados para consumo | Analistas + Negócio | Joia lapidada |

#### Por que essa separação importa para o negócio

- **Rastreabilidade:** sempre é possível voltar ao dado original (Bronze) para investigar inconsistências
- **Confiança progressiva:** o CEO consome Gold (máxima confiança); o engenheiro acessa Bronze para investigação
- **Separação de responsabilidades:** times diferentes cuidam de cada camada, com critérios de qualidade específicos
- **Auditoria:** em caso de erro em um relatório executivo, é possível rastrear o caminho exato do dado até a fonte

---

### 3. Os 4 Componentes de um Ambiente de Big Data

Todo ambiente de Big Data, independentemente do tamanho ou tecnologia, tem quatro funções fundamentais:

| Componente | Função | Perguntas de negócio que dirigem as decisões |
|------------|--------|---------------------------------------------|
| **Ingestão** | Capturar dados de todas as fontes | Com que frequência? Tempo real ou batch diário? Quais fontes priorizar? |
| **Armazenamento** | Guardar com custo eficiente e escalável | Por quanto tempo guardar? Quem pode acessar? Qual nível de redundância? |
| **Processamento** | Transformar, agregar e enriquecer | Com que latência os dados precisam estar disponíveis? Quem processa o quê? |
| **Consumo** | Entregar para usuários e sistemas | Quem precisa de quê, em qual formato e com qual nível de detalhe? |

As decisões técnicas sobre cada componente devem ser dirigidas por perguntas de negócio — não pela tecnologia disponível.

#### Relação com a Arquitetura Medallion

- **Ingestão** alimenta a camada **Bronze**
- **Processamento** transforma Bronze em **Silver** e Silver em **Gold**
- **Consumo** lê da camada **Gold** (relatórios, dashboards, APIs para sistemas)
- **Armazenamento** está presente em todas as camadas, com políticas de custo e retenção diferentes

---

## Exercício Discursivo em Grupo

**Duração:** 70 minutos  
**Grupos:** 4–5 pessoas

### Caso: Arquitetura de Dados do Mercado Livre

O Mercado Livre é a maior plataforma de e-commerce e pagamentos da América Latina, com operações em 18 países, mais de 100 milhões de usuários ativos e cerca de 14 milhões de vendedores. Processa, em pico, mais de 1 milhão de transações por hora.

A plataforma precisa operar simultaneamente em dois regimes:

**Regime transacional (tempo real):** processar pagamentos via Mercado Pago, emitir comprovantes, comunicar vendedores sobre novos pedidos, acionar a logística e atualizar o estoque em segundos.

**Regime analítico (batch e near-real-time):** gerar recomendações de produtos personalizadas para cada usuário, calcular scores de risco de fraude para cada transação antes de aprová-la, ajustar preços dinamicamente conforme oferta e demanda, e produzir relatórios financeiros diários para reguladores em 18 países com regras diferentes.

A equipe de dados do Mercado Livre publica regularmente em seu blog técnico sobre a evolução da arquitetura — partindo de bancos relacionais isolados para uma arquitetura unificada baseada em Data Lakehouse com camadas bem definidas. O desafio contínuo é garantir que os dados estejam disponíveis na qualidade e no tempo certo para cada tipo de consumidor: desde o cientista de dados que treina modelos até o executivo que consulta o dashboard consolidado.

### Questões para análise e discussão

**1. Separação OLTP e OLAP (15 min)**
Identifique, com base na descrição acima, quais operações do Mercado Livre pertencem ao ambiente transacional (OLTP) e quais ao analítico (OLAP). O que aconteceria se a empresa tentasse usar a mesma base de dados para os dois fins?

**2. Arquitetura Medallion na prática (25 min)**
Proponha como a Arquitetura Medallion poderia ser aplicada ao fluxo de dados do Mercado Livre. Para cada camada, descreva:
- Que tipo de dado entraria nessa camada
- Que transformações ocorreriam entre uma camada e a próxima
- Quem seria o consumidor final de cada camada (qual perfil de usuário acessa o quê)

**3. Transferência para o seu setor (30 min)**
Escolha uma organização do setor do grupo (pode ser a empresa de um dos integrantes, uma concorrente conhecida, ou uma referência do setor):
- Essa organização usa Data Warehouse, Data Lake ou ainda está em um nível anterior (planilhas/sistemas isolados)?
- Qual seria o primeiro "caso de uso" que justificaria a migração para uma arquitetura mais moderna?
- Quais fontes de dados alimentariam a camada Bronze nesse caso?
- O que estaria na camada Gold ao final do processo?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca na questão: o que impede as organizações de evoluir sua arquitetura de dados, mesmo quando já sabem que precisam?

---

## Leituras Complementares

- Kimball, R. & Ross, M. (2013). *The Data Warehouse Toolkit* — Capítulo 1 (introdução conceitual).
- Databricks. *What is a Data Lakehouse?* [databricks.com/glossary/data-lakehouse]
- Gartner. *Magic Quadrant for Cloud Database Management Systems* — seção comparativa.

---

## Próxima Aula

➡️ [Aula 4 — Construindo um Data Lake: Estratégia e Decisões](../aula_04/)
