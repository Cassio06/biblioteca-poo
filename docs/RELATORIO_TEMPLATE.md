# Roteiro do Relatório Final e Apresentação — Trabalho da P2

> **Instruções de Entrega (conforme `Trabalho P2.pdf`):**
> - O relatório final deve ser entregue em formato **PDF** no dia anterior à apresentação (apresentações nos dias **23 e 26 de novembro**, conforme cronograma).
> - Extensão mínima exigida: **4 páginas**.
> - Este arquivo serve como esqueleto/template para a redação do documento final da equipe.
> - A seção 6 do edital (6.1 a 6.5) descreve a **apresentação oral**; seus tópicos foram incluídos aqui como roteiro, junto com os itens obrigatórios do relatório (seção 8).

---

## 1. Identificação da Equipe

- **Instituição:** iCEV — Instituto de Ensino Superior
- **Disciplina:** Programação Orientada a Objetos (Trabalho da P2)
- **Tema atribuído:** S10a — Gestão de Consultoria (“Planilha Certa”)
- **Integrantes:**
  - Cezar Gabriel de Souza Vicente Mendes
  - Artur Henrique Da Silva Alencar
  - Lukas Souza Melo
  - Cássio Filipe Meireles De Carvalho Braga

---

## 2. Introdução ao Projeto (Seção 6.1)

- **Visão Geral:** Descrição do problema enfrentado pela empresa de consultoria “Planilha Certa” (planejamento financeiro, gestão empresarial e análise de dados/TI), público-alvo e principais funcionalidades do sistema.
- **Fluxo Geral do Sistema:** Como clientes (`Regular` e `VIP`), consultores, contratos, projetos, etapas e faturas interagem do cadastro até a emissão de relatórios e acúmulo de fidelidade.

---

## 3. Contribuição Individual de Cada Integrante (Seção 8)

*(Detalhar o que cada integrante desenvolveu no projeto)*

| Integrante | Branch | Responsabilidades e Contribuições no Projeto |
| :--- | :--- | :--- |
| **Cássio Filipe Meireles De Carvalho Braga** | `Cassio` | **Core, Entidades e Alocação:** Modelagem base de POO (herança, polimorfismo, abstração e encapsulamento em Clientes, Consultores e Contratos); cadastro de clientes (Regular/VIP com histórico) e consultores por especialização (financeiro, gestão, TI); algoritmo de alocação automática (menor carga, máx. 3 ativos, prioridade VIP). |
| **Artur Henrique Da Silva Alencar** | `Arthur` | **Projetos, Etapas e Prazos:** Gerenciamento de projetos divididos em etapas (análise inicial, implementação, revisão final) com prazos e valores; controle de status das etapas (pendente, em andamento, concluída) e regra de marcação como atrasada; cálculo automático do progresso do projeto. |
| **Cezar Gabriel de Souza Vicente Mendes** | `Cezar` | **Faturamento, Fidelidade e Recomendações:** Pagamento por etapa concluída ou entrega final e emissão de faturas detalhadas (10% de desconto automático para VIP); programa de fidelidade (1 ponto a cada R$ 100 pagos, 100 pontos = 5% de desconto até 15%); recomendação de especializações ainda não contratadas. |
| **Lukas Souza Melo** | `Lukas` | **Persistência, Relatórios PDF e Interface/Erros:** Persistência de dados em arquivos (JSON, CSV ou TXT) e tentativa do desafio Google Drive; emissão de relatórios de desempenho (console e PDF com iText, incluindo recomendações para VIP); menu/interface principal e tratamento de erros. |

---

## 4. Estrutura do Código e Decisões de Design OO (Seção 6.2)

- **Arquitetura de Pacotes:** Organização em `model`, `repository`, `service`, `view` e `util`.
- **Justificativa dos Pilares de POO:**
  - **Abstração:** Como os elementos do domínio da consultoria foram modelados.
  - **Encapsulamento:** Como as regras de limite de projetos por consultor, prazos de etapas e saldo de pontos foram protegidas.
  - **Herança:** Justificativa para a hierarquia de classes adotada (ex.: `ClienteRegular` e `ClienteVIP`).
  - **Polimorfismo:** Como descontos, prioridades e relatórios personalizados foram tratados polimorficamente.
- **Classe de Destaque (Obrigatório no Relatório):**
  - *Inserir aqui o trecho de código ou captura de tela (screenshot) de uma classe considerada importante no projeto e explicar seu funcionamento.*

### 4.1 Demonstração Prática do Sistema (Seção 6.3 — apresentação)
- *Roteiro de demonstração com exemplos reais: cadastro de cliente VIP e Regular → criação de contrato/projeto → alocação automática de consultor → avanço/atraso de etapas e progresso → faturamento com descontos e pontos → relatório de desempenho (console/PDF) com recomendações.*

---

## 5. Funcionalidades Implementadas e Pendentes (Seção 8)

### 5.1 Funcionalidades Concluídas
- [ ] Cadastro de clientes (`Regular`/`VIP`), consultores (`Financeiro`, `Gestão`, `TI`) e contratos.
- [ ] Alocação automática de consultores (menor carga, máx. 3 projetos ativos, prioridade VIP).
- [ ] Gerenciamento de projetos em etapas com prazos, valores, detecção de atraso e cálculo de progresso.
- [ ] Emissão de relatórios de desempenho (com seção extra de recomendações para clientes VIP).
- [ ] Faturamento por etapa ou entrega final com desconto automático de 10% para VIPs.
- [ ] Programa de fidelidade (1 ponto a cada R$ 100 pagos; 5% de desconto a cada 100 pontos até 15%) e recomendação de especializações não contratadas.
- [ ] Persistência em arquivos (`CSV` / `JSON` / `TXT`) e tratamento de erros.

### 5.2 Funcionalidades Não Concluídas e Justificativa
- *(Caso alguma funcionalidade ou o desafio extra do Google Drive não tenha sido concluído, descrever qual foi e o motivo técnico ou de tempo).*

---

## 6. Experiência do Grupo, Desafios e Soluções (Seções 6.4 e 8)

- **Principais dificuldades enfrentadas:** *(Relatar problemas encontrados durante a modelagem, persistência em arquivos, controle de datas/prazos ou integração).*
- **Soluções adotadas:** *(Como a equipe contornou cada desafio).*
- **Aprendizados e experiência individual/coletiva:** *(O que o grupo mais gostou de implementar e o quanto aprendeu).*

---

## 7. Bibliotecas Utilizadas e Motivo das Escolhas (Seção 8)

- **Java Standard Library (`java.time`, `java.nio.file`, `java.math`):** manipulação precisa de prazos (`LocalDate`), valores monetários (`BigDecimal`) e leitura/escrita de arquivos.
- **Biblioteca de Persistência (ex.: Gson / Jackson / OpenCSV):** *(Justificar a escolha quando definida).*
- **Biblioteca de Relatórios PDF (ex.: iText):** *(Recomendada no edital da P2 para exportação de relatórios em PDF).*

---

## 8. Conclusão e Melhorias Futuras (Seção 6.5)

- Sugestões de extensões futuras para o sistema da “Planilha Certa” (ex.: interface gráfica web/desktop, notificações automáticas de etapas próximas do vencimento, dashboard financeiro e sincronização em nuvem).

---

## 9. Referências Consultadas (Seção 8)

- *(Listar links da documentação oficial do Java, tutoriais, fóruns, issues e materiais de aula consultados durante o desenvolvimento).*
