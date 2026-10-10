# Aula 6 — Governança, Privacidade e LGPD

**Disciplina:** Data Science e Big Data — MBA Mackenzie
**Duração:** 4 horas

---

## Objetivos de Aprendizagem

Ao final desta aula, o aluno será capaz de:

1. Definir Governança de Dados e diferenciá-la de gerenciamento de TI
2. Identificar e aplicar os papéis centrais em um modelo de governança de dados
3. Compreender os principais impactos práticos da LGPD em operações de dados
4. Classificar dados pessoais e sensíveis e selecionar a base legal adequada para cada tratamento
5. Explicar o conceito de Data Mesh como modelo de governança distribuída
6. Elaborar uma política básica de controle de acesso a dados

---

## Estrutura da Aula (4 horas)

| Bloco | Conteúdo | Duração |
|-------|----------|---------|
| Teoria — Governança de dados | Conceito, papéis e estruturas | 40 min |
| Teoria — LGPD na prática | Tipos de dados, bases legais e obrigações | 40 min |
| Intervalo | — | 10 min |
| Teoria — Data Mesh | Governança federada e descentralização | 25 min |
| Intervalo | — | 10 min |
| Exercício discursivo em grupo | Análise de caso real: Vazamento de dados da Claro/Embratel | 75 min |
| Encerramento | Síntese e leituras | 20 min |

---

## Conteúdo Teórico

### 1. Governança de Dados

#### O que é governança de dados

Governança de Dados é o **conjunto de políticas, processos, papéis e responsabilidades** que determina quem pode fazer o quê com quais dados — e como as decisões sobre dados são tomadas dentro da organização.

| Governança NÃO é | Governança É |
|-----------------|-------------|
| Apenas segurança de TI (firewall, criptografia) | Definir quem decide o que os dados significam |
| Apenas qualidade de dados | Definir quem autoriza o acesso a quais dados |
| Apenas compliance regulatório | Definir quem é responsável quando um dado está errado |
| Responsabilidade exclusiva da TI | Definir quais dados podem ser cruzados e sob quais condições |

#### Papéis e responsabilidades

| Papel | Perfil típico | Responsabilidade principal |
|-------|--------------|---------------------------|
| **Chief Data Officer (CDO)** | C-Level | Estratégia de dados, ROI, cultura data-driven |
| **Data Owner** | Diretor de área | Responsável pelo dado do seu domínio: define regras, autoriza acessos, aprova qualidade |
| **Data Steward** | Analista sênior da área | Cuida do dado no dia a dia: cataloga, documenta, monitora qualidade |
| **Data Custodian** | TI / Engenharia de Dados | Armazena e implementa os controles definidos pelo negócio — executa, não decide |
| **DPO (Data Protection Officer)** | Jurídico / Compliance | Garante conformidade com LGPD; ponto de contato com a ANPD |

**Regra fundamental:** O Data Owner decide a política. O Data Custodian implementa. O DPO garante a legalidade. Quando essas responsabilidades se confundem, a governança falha.

#### Modelos de maturidade em governança

| Nível | Características |
|-------|----------------|
| 0 — Inexistente | Sem políticas; cada área faz o que quer com os dados |
| 1 — Reativo | Políticas surgem após incidentes; gestão apagando incêndio |
| 2 — Definido | Políticas documentadas; papéis definidos informalmente |
| 3 — Gerenciado | Políticas aplicadas com monitoramento; papéis formalizados |
| 4 — Otimizado | Governança automatizada, medida e continuamente aprimorada |

---

### 2. LGPD — O que Todo Gestor Precisa Saber

#### Tipos de dados pessoais

| Tipo | Definição | Exemplos |
|------|-----------|----------|
| **Dado pessoal** | Identifica ou pode identificar uma pessoa natural | Nome, CPF, e-mail, endereço, IP, número de telefone |
| **Dado sensível** | Pode gerar discriminação ou é de natureza íntima | Saúde, genética, biometria, religião, orientação sexual, origem racial |
| **Dado anonimizado** | Não permite identificação nem com esforço razoável | Estatísticas sem identificador individual |

Dado sensível exige bases legais mais restritas e controles técnicos adicionais. O tratamento inadequado sujeita a organização às penalidades mais severas da lei.

#### Bases legais — por que posso tratar este dado?

Todo tratamento de dados pessoais precisa de uma base legal. Sem base legal definida, o tratamento é ilegal, independentemente da utilidade do dado.

| Base legal | Quando usar | Exemplo prático |
|-----------|-------------|-----------------|
| **Consentimento** | Usuário autorizou expressamente, de forma específica e informada | Marketing por e-mail, uso de cookies de rastreamento |
| **Contrato** | Necessário para executar o contrato com o titular | Dados de entrega para uma compra online |
| **Obrigação legal** | A lei exige o tratamento | Nota fiscal, eSocial, dados à Receita Federal |
| **Interesse legítimo** | Interesse razoável do controlador, sem prejudicar o titular | Análise interna de risco de crédito, prevenção a fraudes |
| **Tutela da saúde** | Proteção da vida ou saúde por profissional de saúde | Histórico clínico para tratamento médico |

#### 7 obrigações práticas da LGPD para gestores de dados

1. **Mapeamento:** saber quais dados pessoais você trata, onde estão armazenados e por quê
2. **Minimização:** coletar apenas o necessário para a finalidade declarada
3. **Finalidade:** usar os dados só para o propósito informado ao titular — não reutilizar para outros fins
4. **Segurança:** implementar medidas técnicas e organizacionais para proteger os dados
5. **Transparência:** informar os titulares sobre como seus dados são tratados
6. **Direitos do titular:** responder solicitações de acesso, correção e exclusão em até 15 dias
7. **Incidentes:** notificar a ANPD e os titulares afetados em caso de vazamento, no prazo legal

**Penalidades:** até 2% do faturamento do grupo econômico no Brasil no último exercício, limitado a R$ 50 milhões por infração.

---

### 3. Data Mesh — Governança Descentralizada

O modelo centralizado de governança não escala em organizações grandes: um time central vira gargalo e as áreas de negócio ficam bloqueadas esperando aprovações.

**Data Mesh** é um modelo arquitetural e organizacional que trata domínios de negócio como responsáveis pelos seus próprios dados — como produtos.

| Princípio | O que significa |
|-----------|----------------|
| **Domínios como donos** | Cada área de negócio é responsável pelos dados que gera e disponibiliza |
| **Dados como produto** | Cada domínio trata seu dado como produto: com qualidade garantida, SLA, documentação e suporte |
| **Infraestrutura como plataforma** | TI central fornece ferramentas; os domínios decidem como usá-las |
| **Governança federada** | Padrões e políticas centrais (ex.: LGPD, qualidade mínima); execução descentralizada |

**Quando considerar Data Mesh:**
- Empresa grande com muitas áreas produzindo dados independentemente
- O time central de dados virou gargalo para o negócio
- Áreas de negócio querem mais autonomia analítica mas com qualidade garantida

---

## Exercício Discursivo em Grupo

**Duração:** 75 minutos  
**Grupos:** 4–5 pessoas

### Caso: Vazamento de Dados na Claro Brasil — ANPD 2023

Em 2023, a Agência Nacional de Proteção de Dados (ANPD) abriu processo administrativo sancionador contra a Claro Brasil S.A. após incidente de segurança que resultou no vazamento de dados pessoais de clientes. O incidente envolveu acesso não autorizado a sistemas da empresa, expondo informações como nome, CPF, endereço, dados de contrato e histórico de consumo de serviços de telecomunicações de um número significativo de titulares.

A investigação da ANPD identificou deficiências nos controles de acesso interno: funcionários e prestadores de serviços tinham acesso a volumes de dados muito superiores ao necessário para suas funções (violação do princípio da minimização e do controle de acesso por necessidade). Além disso, a empresa não havia implementado monitoramento adequado de acessos atípicos a grandes volumes de dados, e o processo de notificação de titulares após o incidente foi considerado insuficiente pela agência.

O caso foi relevante por ser um dos primeiros processos sancionadores de grande porte conduzidos pela ANPD, sinalizando o início de uma fase de aplicação efetiva da lei.

*Fontes: notícias publicadas nos portais Convergência Digital, Teletime e no site da ANPD (gov.br/anpd). Os valores das penalidades são objeto do processo em curso.*

### Questões para análise e discussão

**1. Diagnóstico de governança (20 min)**
Com base nas deficiências descritas no caso, identifique quais princípios da LGPD foram violados e qual papel de governança (CDO, Data Owner, Data Custodian, DPO) estava ausente ou funcionando inadequadamente. Justifique sua análise.

**2. Controles que teriam evitado o incidente (25 min)**
Proponha, de forma concreta, quais controles de governança teriam prevenido ou limitado o impacto do incidente. Para cada controle proposto, especifique:
- O que o controle faz
- Quem é responsável por implementá-lo (papel de governança)
- Qual princípio da LGPD ele endereça

**3. Transferência para o seu setor (30 min)**
Empresas de telecomunicações não são as únicas com esse tipo de risco. Identifique no setor do grupo:
- Quais dados pessoais (ou sensíveis) são tratados pela organização?
- Qual é a base legal para cada tratamento?
- Quais são os 3 maiores riscos de violação de dados nesse setor?
- Quais controles de governança estão ausentes ou insuficientes na maioria das organizações desse setor?

### Apresentação e debate
Cada grupo apresenta a questão 3 (5 minutos). O debate foca na questão: privacidade como barreira ao uso de dados vs. privacidade como condição para que o uso de dados seja sustentável — qual perspectiva gera mais valor para o negócio no longo prazo?

---

## Leituras Complementares

- ANPD. *Guia Orientativo para Definições dos Agentes de Tratamento* [gov.br/anpd]
- Lei 13.709/2018 — LGPD — Art. 11 (dados sensíveis) e Art. 18 (direitos do titular)
- Dehghani, Z. (2022). *Data Mesh: Delivering Data-Driven Value at Scale* — Capítulos 1 e 2 (O'Reilly)

---

## Próxima Aula

➡️ [Aula 7 — Roadmap Data-Driven: do Conceito à Execução](../aula_07/)
