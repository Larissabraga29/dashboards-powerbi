# Análise e Modelagem de Dados – Dashboard de Vendas

## 🧩 Problemas encontrados nos dados
- IDs duplicados na tabela de produtos e pedidos.
- Relacionamentos não estavam sendo detectados automaticamente.

## 🔍 Etapas realizadas
- Abertura no Power Query e remoção de duplicadas com `Table.Distinct`.
- Verificação de cardinalidade para criar os relacionamentos corretos.
- Criação de colunas com linguagem DAX (básico) para cálculo de Lucro e Margem.
- Testes de diferentes tipos de gráficos (Treemap, Cascata, KPI, Linha) para responder às perguntas do desafio e treinar.

## ✅ Conclusão
O modelo só passou a funcionar corretamente após:
- Limpeza e modelagem dos dados no Power Query.
- Ajustes manuais nos relacionamentos entre as tabelas.
