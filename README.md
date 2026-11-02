# Planilha Certa — Sistema de Gestão de Consultoria (POO)

Sistema de gerenciamento de consultoria empresarial em Java, desenvolvido como projeto acadêmico da disciplina de **Programação Orientada a Objetos** (Trabalho da P2).

> **Nota sobre o repositório:** O projeto foi inicialmente esboçado com o tema genérico de Biblioteca e atualizado para atender ao enunciado oficial sorteado/atribuído à equipe: **S10a — Gestão de Consultoria ("Planilha Certa")**.

---

## Objetivo e Contexto do Problema

A empresa de consultoria **“Planilha Certa”** oferece serviços personalizados de **planejamento financeiro**, **gestão empresarial** e **análise de dados (TI)** para diversos clientes.

O objetivo deste sistema é gerenciar o cadastro de clientes, consultores, contratos de consultoria e o controle de projetos e suas etapas. Clientes **VIP** possuem atendimento prioritário, descontos exclusivos e relatórios personalizados com recomendações. Cada projeto é dividido em etapas com prazos e valores específicos, permitindo monitorar o progresso, faturar por etapa ou na entrega final, acumular pontos em um programa de fidelidade e emitir relatórios de desempenho.

---

## Status do Projeto

🚧 **Em fase de estruturação e modelagem (Esqueleto do Projeto).**  
A arquitetura de diretórios, documentação de requisitos e modelagem inicial estão definidas. A implementação do código-fonte em Java será realizada nas próximas etapas.

---

## Requisitos do Sistema

### 1. Cadastro de Clientes, Consultores e Contratos
- **Clientes:** registro com categoria (`Regular` ou `VIP`) e histórico de contratos anteriores.
- **Consultores:** cadastro com especialização (`Financeiro`, `Gestão`, `TI`) e **alocação automática** a projetos (seleciona o consultor da especialização exigida com menos projetos ativos, respeitando o limite máximo de **3 projetos ativos por consultor**).
- **Contratos:** gerenciamento de prazos, valores e forma de pagamento; projetos de clientes **VIP** possuem prioridade na alocação de consultores.

### 2. Gerenciamento de Projetos e Etapas
- **Divisão em etapas:** cada projeto contém etapas (ex.: *análise inicial*, *implementação*, *revisão final*), cada uma com prazo e valor definidos.
- **Controle de status:** acompanhamento de cada etapa (`Pendente`, `Em andamento`, `Concluída`). Etapas não concluídas após o prazo passam automaticamente a constar como `Atrasada`.
- **Cálculo de progresso:** percentual calculado pela razão $\text{etapas concluídas} \div \text{total de etapas}$.

### 3. Relatórios e Desempenho do Projeto
- **Relatório de desempenho:** emissão detalhada contendo o status, prazo e progresso de cada etapa do projeto (console e/ou PDF com *iText*).
- **Personalização VIP:** relatórios destinados a clientes VIP incluem uma **seção adicional de recomendações** de serviços.

### 4. Pagamentos e Faturamento
- **Modalidades de pagamento:** pagamento realizado por etapa concluída ou na entrega final, conforme estipulado no contrato.
- **Faturas detalhadas:** emissão de faturas com aplicação automática de **10% de desconto** para clientes VIP.

### 5. Programa de Fidelidade e Retenção de Clientes
- **Acúmulo de pontos:** 1 ponto a cada **R$ 100,00** pagos.
- **Desconto progressivo:** cada **100 pontos** acumulados concedem **5% de desconto** no próximo contrato, limitado ao teto máximo de **15%**.
- **Histórico e recomendação:** consulta ao histórico de projetos do cliente e recomendação automática de serviços das especializações que ele ainda não contratou.

### Checklist de Requisitos Obrigatórios
- [ ] Cadastro completo de clientes, consultores e contratos de consultoria.
- [ ] Gerenciamento de projetos com etapas, prazos e status de progresso.
- [ ] Alocação automática de consultores, com prioridade para clientes VIP.
- [ ] Emissão de relatórios de desempenho com personalização para VIPs.
- [ ] Pagamentos e faturamento por etapa/entrega, com aplicação de descontos automáticos.
- [ ] Programa de fidelidade com pontos, histórico de projetos e recomendações.
- [ ] Persistência de dados em arquivos (`CSV`, `JSON` ou `TXT`).
- [ ] Tratamento de erros (entradas inválidas e arquivos ausentes não devem interromper o fluxo principal).

---

## Programação Orientada a Objetos (POO)

O projeto aplica os quatro pilares de POO de maneira justificada no domínio da consultoria:

- **Abstração:** representação das entidades essenciais do negócio (`Cliente`, `Consultor`, `Contrato`, `Projeto`, `Etapa`, `Fatura`, `RelatorioDesempenho`).
- **Encapsulamento:** proteção do estado interno das classes (ex.: saldo de pontos de fidelidade, limite de 3 projetos ativos por consultor, transição de status de etapas e validação de prazos/valores) exposto apenas por métodos de negócio seguros.
- **Herança:** especialização de tipos de clientes (`Cliente` $\rightarrow$ `ClienteRegular` e `ClienteVIP`) e/ou base comum de pessoas (`Pessoa` $\rightarrow$ `Cliente`, `Consultor`), reaproveitando atributos e comportamentos compartilhados.
- **Polimorfismo:** comportamentos distintos conforme o tipo concreto do cliente ou modalidade de cobrança — como cálculo polimórfico de descontos em faturas (VIP vs. Regular + pontos de fidelidade), prioridade de alocação e geração de relatórios de desempenho (inclusão automática da seção de recomendações para `ClienteVIP`).

Detalhes adicionais sobre os pacotes e classes planejados encontram-se em [`docs/MODELAGEM.md`](docs/MODELAGEM.md).

---

## Estrutura do Repositório

```text
biblioteca-poo/
├── data/                                    # Arquivos de persistência (CSV/JSON/TXT)
│   └── README.md
├── docs/                                    # Documentação de arquitetura e relatório acadêmico
│   ├── MODELAGEM.md                         # Esqueleto da arquitetura, pacotes e classes POO
│   └── RELATORIO_TEMPLATE.md                # Estrutura base para o Relatório Final (P2)
├── src/                                     # Diretório de código-fonte (esqueleto de pacotes)
│   ├── main/java/br/com/planilhacerta/
│   │   ├── model/                           # Entidades de domínio e enums
│   │   ├── repository/                      # Persistência em arquivos (CSV/JSON/TXT)
│   │   ├── service/                         # Regras de negócio (alocação, faturamento, fidelidade)
│   │   ├── view/                            # Interface com o usuário (Console / Desktop / Web)
│   │   └── util/                            # Utilitários, validadores, gerador de PDF e exceções
│   └── test/java/br/com/planilhacerta/      # Testes unitários e de integração planejados
├── .env.example                             # Exemplo de variáveis de ambiente (ex.: integração Google Drive)
├── .gitignore                               # Arquivos ignorados pelo Git
├── README.md                                # Documentação principal do projeto
├── S10a - Gestão de Consultoria.docx.pdf    # Enunciado específico da equipe (Planilha Certa)
└── Trabalho P2.pdf                          # Diretrizes gerais e critérios de avaliação da P2
```

---

## Tecnologias e Decisões Técnicas

- **Linguagem:** Java. *(Versão do JDK a ser definida pelo grupo — sugestão: JDK 17 LTS ou superior. O edital não exige versão específica.)*
- **Persistência:** Arquivos locais (`CSV`, `JSON` ou `TXT`) armazenados no diretório [`data/`](data/).
  - *Desafio extra opcional:* sincronização/armazenamento dos arquivos de dados no Google Drive.
- **Relatórios:** Saída formatada no console e recomendação de uso da biblioteca **iText** para exportação em PDF.
- **Interface:** Console interativo (ou Desktop/Web simples), priorizando clareza de fluxo e validação de entradas.

---

## Como Executar

> ⚠️ *O código-fonte ainda não foi implementado. As instruções abaixo representam o fluxo previsto quando o desenvolvimento for iniciado.*

1. **Pré-requisitos:**
   - Java JDK instalado (versão a confirmar pelo grupo; sugestão: 17 ou superior).
   - Git instalado.
2. **Configuração de ambiente (opcional):**
   - Copie o arquivo `.env.example` para `.env` caso utilize credenciais externas (como API do Google Drive).
3. **Compilação e execução (prevista):**
   ```bash
   # Compilar os arquivos Java (quando implementados)
   javac -d out $(find src/main/java -name "*.java")

   # Executar a aplicação principal
   java -cp out br.com.planilhacerta.Main
   ```
   *(Caso o grupo adote Maven ou Gradle na etapa de codificação, os comandos `mvn compile exec:java` ou `./gradlew run` serão atualizados nesta seção).*

---

## Equipe e Divisão de Responsabilidades (Branches)

O desenvolvimento está organizado em branches individuais a partir da `main`, garantindo que cada integrante tenha seu ambiente de trabalho estruturado:

### 👤 Cássio Filipe Meireles De Carvalho Braga — Branch: `Cassio`
**Escopo: Core, Entidades e Alocação**
- Modelagem base de POO (herança, polimorfismo, abstração e encapsulamento nas classes de Clientes, Consultores e Contratos).
- Cadastro de clientes (`Regular` e `VIP` com histórico) e consultores por especialização (`Financeiro`, `Gestão`, `TI`).
- Algoritmo de alocação automática: escolher o consultor da área com menos projetos ativos (máx. 3), dando prioridade para clientes VIP.

### 👤 Artur Henrique Da Silva Alencar — Branch: `Arthur`
**Escopo: Projetos, Etapas e Prazos**
- Gerenciamento de projetos divididos em etapas (*análise inicial*, *implementação*, *revisão final*) com prazos e valores.
- Controle de status das etapas (`Pendente`, `Em andamento`, `Concluída`) e regra para marcar como `Atrasada` se passar do prazo.
- Cálculo automático do progresso do projeto ($\text{etapas concluídas} \div \text{total de etapas}$).

### 👤 Cezar Gabriel de Souza Vicente Mendes — Branch: `Cezar`
**Escopo: Faturamento, Fidelidade e Recomendações**
- Pagamento por etapa concluída ou entrega final + emissão de faturas detalhadas (com 10% de desconto automático para VIP).
- Programa de Fidelidade: 1 ponto a cada R$ 100,00 pagos (100 pontos = 5% de desconto no próximo contrato, limite de 15%).
- Sistema de recomendação sugerindo serviços de especializações que o cliente ainda não contratou.

### 👤 Lukas Souza Melo — Branch: `Lukas`
**Escopo: Persistência, Relatórios PDF e Interface/Erros**
- Persistência de dados em arquivos (`JSON`, `CSV` ou `TXT`) + tentativa do desafio extra de salvar no Google Drive.
- Emissão de relatórios de desempenho (console e PDF com *iText*), incluindo a seção extra de recomendações para clientes VIP.
- Criação do menu/interface principal e tratamento de erros (evitar que o sistema quebre com entradas inválidas ou arquivos ausentes).

---

## Entregas Acadêmicas e Cronograma

- **Datas das apresentações:** **23 e 26 de novembro** (cada grupo apresenta na data designada no cronograma a ser divulgado previamente).
- **Entrega no dia anterior à apresentação** (apenas):
  1. **Código-fonte do projeto** neste repositório Git com instruções de execução atualizadas no `README.md`.
  2. **Relatório final em PDF** (mínimo de 4 páginas), cujo roteiro base está preparado em [`docs/RELATORIO_TEMPLATE.md`](docs/RELATORIO_TEMPLATE.md).
- Não é necessário entregar executável binário — apenas código-fonte e relatório.
- **Tamanho do grupo:** individual ou até no máximo 5 pessoas.
- **Envio da composição do grupo:** `samuel.oliveira@grupocev.com`.

### Dimensões Avaliadas

Código · Abstrações OO · Completude e Corretude Funcional · Tratamento de Erros · Diferencial do Projeto · Avaliação Individual · Trabalho em Grupo · Defesa Oral.

Critérios detalhados no edital: estrutura e design do código (modularidade, coesão, acoplamento), implementação dos requisitos funcionais, funcionalidades adicionais e criatividade, qualidade do código e boas práticas (nomenclatura, comentários, **testes**, padrões) e tratamento de erros.
