# Ambiente de Trabalho — Branch `Arthur`

**Responsável:** Artur Henrique Da Silva Alencar  
**Módulo:** Projetos, Etapas e Prazos

---

## 🎯 Escopo de Responsabilidades

1. **Gerenciamento de Projetos e Divisão em Etapas:**
   - Estruturar cada projeto em etapas (ex.: *análise inicial*, *implementação*, *revisão final*), cada uma com prazo (`LocalDate`) e valor (`BigDecimal`) definidos.
2. **Controle de Status e Verificação de Prazos:**
   - Controlar os status de cada etapa: `Pendente`, `Em andamento`, `Concluída`.
   - Implementar a regra automática que altera o status para `Atrasada` caso a etapa não esteja concluída após a data de prazo estipulada.
3. **Cálculo Automático de Progresso:**
   - Calcular o progresso do projeto pela fórmula:
     $$\text{Progresso} = \frac{\text{Etapas Concluídas}}{\text{Total de Etapas}}$$

---

## 📂 Arquivos Planejados para esta Branch (Sem código ainda)

### Pacote `src/main/java/br/com/planilhacerta/model/`
- [ ] `StatusEtapa.java` *(enum: `PENDENTE`, `EM_ANDAMENTO`, `CONCLUIDA`, `ATRASADA`)*
- [ ] `Etapa.java` *(classe com nome/descrição, prazo, valor, status e método de verificação de atraso)*
- [ ] `Projeto.java` *(classe com lista de etapas, consultor alocado, especialização exigida e cálculo de progresso)*

### Pacote `src/main/java/br/com/planilhacerta/service/`
- [ ] `ProjetoService.java` *(gerenciamento de projetos, adição/edição de etapas, atualização de status, verificação de atrasos por data e consulta de percentual de conclusão)*

---

## 🤝 Pontos de Integração com a Equipe

- **Com `Cassio` (Core e Alocação):** `Projeto` recebe o `Consultor` selecionado pelo `AlocacaoService` e compõe o `Contrato` do `Cliente`.
- **Com `Cezar` (Faturamento):** A conclusão de uma `Etapa` ou de todas as etapas do `Projeto` dispara a geração de faturas (`POR_ETAPA` ou `ENTREGA_FINAL`).
- **Com `Lukas` (Relatórios e Persistência):** O progresso do projeto e o detalhamento de cada etapa (status e prazo) alimentam os relatórios de desempenho em console e PDF.
