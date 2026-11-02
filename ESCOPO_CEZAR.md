# Ambiente de Trabalho — Branch `Cezar`

**Responsável:** Cezar Gabriel de Souza Vicente Mendes  
**Módulo:** Faturamento, Fidelidade e Recomendações

---

## 🎯 Escopo de Responsabilidades

1. **Pagamentos e Faturamento:**
   - Suportar faturamento **por etapa concluída** ou **na entrega final**, conforme estipulado no contrato.
   - Emitir faturas detalhadas aplicando automaticamente **10% de desconto para clientes VIP**.
2. **Programa de Fidelidade:**
   - Acumular **1 ponto a cada R$ 100,00 pagos** pelo cliente.
   - Converter cada **100 pontos acumulados em 5% de desconto** no próximo contrato, respeitando o **limite máximo de 15%**.
3. **Sistema de Recomendação de Serviços:**
   - Consultar o histórico de projetos do cliente e identificar as especializações (`Financeiro`, `Gestão`, `TI`) que ele **ainda não contratou**, gerando recomendações personalizadas.

---

## 📂 Arquivos Planejados para esta Branch (Sem código ainda)

### Pacote `src/main/java/br/com/planilhacerta/model/`
- [ ] `ModalidadePagamento.java` *(enum: `POR_ETAPA`, `ENTREGA_FINAL`)*
- [ ] `Fatura.java` *(classe com itens cobrados, valor bruto, desconto VIP, desconto fidelidade, valor líquido e data de emissão)*

### Pacote `src/main/java/br/com/planilhacerta/service/`
- [ ] `FaturamentoService.java` *(geração de faturas por etapa ou entrega final, registro de pagamento e cálculo de desconto VIP de 10%)*
- [ ] `FidelidadeService.java` *(cálculo e crédito de 1 ponto a cada R$ 100 pagos; cálculo de desconto de 5% a 15% para novos contratos)*
- [ ] `RecomendacaoService.java` *(análise do histórico de contratos/projetos do cliente para sugerir especializações ainda não contratadas)*

---

## 🤝 Pontos de Integração com a Equipe

- **Com `Cassio` (Core e Contratos):** Utiliza `Cliente` (`Regular`/`VIP`) e `Contrato` para aplicar os descontos e consultar o histórico de contratações.
- **Com `Arthur` (Projetos e Etapas):** Verifica o status `CONCLUIDA` das etapas/projetos e seus respectivos valores para liberar o faturamento.
- **Com `Lukas` (Relatórios e Persistência):** Fornece as recomendações geradas pelo `RecomendacaoService` para compor a seção extra exclusiva dos relatórios de clientes VIP.
