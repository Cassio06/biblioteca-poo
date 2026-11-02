# Diretório de Persistência (`data/`)

Este diretório armazena os arquivos de dados utilizados pelo sistema **Planilha Certa** (em formato `CSV`, `JSON` ou `TXT`, conforme exigido nas diretrizes do `Trabalho P2.pdf`).

## Arquivos Previstos
- `clientes.(csv|json|txt)` — Cadastro de clientes Regular e VIP, saldo de pontos de fidelidade e histórico.
- `consultores.(csv|json|txt)` — Cadastro de consultores por especialização (`Financeiro`, `Gestão`, `TI`) e projetos alocados.
- `contratos.(csv|json|txt)` — Contratos celebrados, prazos, valores e modalidade de pagamento.
- `projetos.(csv|json|txt)` — Projetos, etapas, prazos, valores e status (`Pendente`, `Em andamento`, `Concluída`, `Atrasada`).
- `faturas.(csv|json|txt)` — Registro de faturamentos por etapa ou entrega final e descontos aplicados.
- `reports/` — Diretório destinado aos relatórios de desempenho exportados (ex.: arquivos PDF gerados com *iText*).

> **Nota sobre Tratamento de Erros:** O sistema deverá inicializar normalmente mesmo que estes arquivos ainda não existam, criando-os sob demanda.
