# Ambiente de Trabalho — Branch `Lukas`

**Responsável:** Lukas Souza Melo  
**Módulo:** Persistência, Relatórios PDF e Interface/Erros

---

## 🎯 Escopo de Responsabilidades

1. **Persistência de Dados e Desafio Google Drive:**
   - Salvar e recuperar dados do sistema em arquivos (`JSON`, `CSV` ou `TXT`) no diretório `data/`.
   - Estruturar/tentar o **desafio extra** de sincronizar ou armazenar os arquivos de dados no **Google Drive**.
2. **Emissão de Relatórios de Desempenho:**
   - Gerar relatórios de desempenho do projeto com detalhes de cada etapa (status, prazo e progresso) tanto no **console** quanto em **PDF (usando a biblioteca iText)**.
   - Incluir uma **seção adicional de recomendações** nos relatórios destinados a clientes **VIP**.
3. **Menu Principal / Interface e Tratamento de Erros:**
   - Criar o menu interativo principal integrando todos os módulos do sistema.
   - Garantir tratamento robusto de erros: o sistema **não deve quebrar** diante de entradas inválidas do usuário ou arquivos de dados ausentes/corrompidos.

---

## 📂 Arquivos Planejados para esta Branch (Sem código ainda)

### Pacote `src/main/java/br/com/planilhacerta/repository/`
- [ ] `RepositorioArquivo.java` *(interface ou classe genérica para leitura/escrita em JSON, CSV ou TXT)*
- [ ] `ClienteRepository.java`, `ConsultorRepository.java`, `ContratoRepository.java`, `ProjetoRepository.java`, `FaturaRepository.java`
- [ ] `GoogleDriveSyncService.java` *(integração opcional do desafio extra para salvar os dados no Google Drive)*

### Pacote `src/main/java/br/com/planilhacerta/util/`
- [ ] `RelatorioDesempenhoGenerator.java` *(formatação no console e geração de PDF com iText, adicionando seção de recomendações para clientes VIP)*
- [ ] `ValidadorEntrada.java` *(leitura segura de números, datas e textos no console sem lançar exceções não tratadas)*
- [ ] `PersistenciaException.java` / `RegraNegocioException.java` *(exceções customizadas para tratamento limpo de erros)*

### Pacote `src/main/java/br/com/planilhacerta/view/`
- [ ] `MenuPrincipalView.java` *(fluxo de navegação entre Clientes, Consultores, Contratos, Projetos/Etapas, Faturamento e Relatórios)*
- [ ] `Main.java` *(ponto de entrada do sistema com inicialização dos repositórios e tratamento global de erros)*

---

## 🤝 Pontos de Integração com a Equipe

- **Com `Cassio` (Core e Alocação):** Persiste e exibe no menu os cadastros de Clientes, Consultores, Contratos e a alocação automática.
- **Com `Arthur` (Projetos e Etapas):** Persiste o estado dos projetos/etapas e consome o cálculo de progresso e prazos para gerar o Relatório de Desempenho.
- **Com `Cezar` (Faturamento, Fidelidade e Recomendações):** Persiste as faturas, exibe descontos/pontos no menu e consome o `RecomendacaoService` para preencher a seção exclusiva de clientes VIP nos relatórios em PDF/console.
