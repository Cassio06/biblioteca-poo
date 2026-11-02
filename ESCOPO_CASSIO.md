# Ambiente de Trabalho — Branch `Cassio`

**Responsável:** Cássio Filipe Meireles De Carvalho Braga  
**Módulo:** Core, Entidades e Alocação

---

## 🎯 Escopo de Responsabilidades

1. **Modelagem Base de POO:**
   - Aplicar de forma justificada **Herança**, **Polimorfismo**, **Abstração** e **Encapsulamento** nas classes centrais de `Cliente`, `Consultor` e `Contrato`.
2. **Cadastro de Clientes, Consultores e Contratos:**
   - Registro de clientes nas categorias `Regular` e `VIP`, mantendo o histórico de contratos anteriores.
   - Cadastro de consultores classificados por especialização (`Financeiro`, `Gestão`, `TI`).
   - Gerenciamento de contratos com prazos, valores e modalidade de pagamento.
3. **Algoritmo de Alocação Automática de Consultores:**
   - Selecionar automaticamente o consultor da especialização exigida que possua **menos projetos ativos**.
   - Respeitar o limite máximo de **3 projetos ativos por consultor**.
   - Garantir **prioridade de alocação** para projetos de clientes **VIP**.

---

## 📂 Arquivos Planejados para esta Branch (Sem código ainda)

### Pacote `src/main/java/br/com/planilhacerta/model/`
- [ ] `Pessoa.java` *(classe abstrata base para Cliente e Consultor)*
- [ ] `CategoriaCliente.java` *(enum: `REGULAR`, `VIP`)*
- [ ] `Cliente.java` *(classe abstrata com histórico de contratos e pontos de fidelidade)*
- [ ] `ClienteRegular.java` *(subclasse com regras padrão)*
- [ ] `ClienteVIP.java` *(subclasse com prioridade de alocação e 10% de desconto em faturas)*
- [ ] `Especializacao.java` *(enum: `FINANCEIRO`, `GESTAO`, `TI`)*
- [ ] `Consultor.java` *(classe com especialização e lista/controle de até 3 projetos ativos)*
- [ ] `Contrato.java` *(classe associando Cliente, Projeto, prazo, valor e modalidade de pagamento)*

### Pacote `src/main/java/br/com/planilhacerta/service/`
- [ ] `ClienteService.java` *(CRUD e consulta de histórico de contratos)*
- [ ] `ConsultorService.java` *(CRUD e listagem por especialização/disponibilidade)*
- [ ] `ContratoService.java` *(criação e gerenciamento de contratos)*
- [ ] `AlocacaoService.java` *(algoritmo de alocação automática com prioridade VIP e teto de 3 projetos)*

---

## 🤝 Pontos de Integração com a Equipe

- **Com `Arthur` (Projetos e Etapas):** `Contrato` e `Consultor` se vinculam à classe `Projeto` criada na branch `Arthur`.
- **Com `Cezar` (Faturamento e Fidelidade):** `Cliente` e `Contrato` fornecem os dados de categoria (`VIP`/`Regular`), histórico de especializações contratadas e saldo de pontos.
- **Com `Lukas` (Persistência, Relatórios e UI):** Os serviços (`ClienteService`, `ConsultorService`, `ContratoService`, `AlocacaoService`) serão consumidos pelo menu principal e persistidos em arquivo.
