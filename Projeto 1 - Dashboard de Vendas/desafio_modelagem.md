# 📊 Resumo de Modelagem e Análise de Dados no Power BI

Este projeto teve como base o desafio de responder 5 perguntas de negócio com base em uma base de dados de vendas, utilizando o Power BI.

## 📌 Etapas realizadas

### 1. **Tratamento de dados no Power Query (Linguagem M)**
- Remoção de duplicadas;
- Ajuste de tipos de dados;
- Padronização de campos (ex: datas, nomes);
- Criação da base `Pedidos` limpa para relacionamento.

### 2. **Modelagem de Dados**
- Identificação de chaves primárias;
- Criação de relacionamento entre as tabelas:
  - Ex: Muitos para um entre `Vendas[Produto]` e `Produtos[ID Produto]`;
- Entendimento da **cardinalidade** entre as tabelas;
- Organização do modelo em estrela (fato e dimensão).

### 3. **Criação de Métricas (DAX)**
- `Lucro = Valor Venda - Custo Envio`
- `MargemLucro = DIVIDE(Lucro, Valor Venda) * 100`
- Média de valor de venda para KPI de Abril/2014

### 4. **Análises Visuais**
- Gráfico de cascata: valor por tipo de envio;
- Treemap: custo médio por mercado;
- KPI: comparação com meta mensal;
- Linha: margem de lucro ao longo do tempo;
- Donut: lucro médio por categoria.

## Resumos Visuais
Os aprendizados de conceitos como Big Data, Modelagem, Linguagem M, DAX e Cardinalidade estão disponíveis na pasta `resumos/`.

## ✅ Conclusão
Este painel demonstrou como é possível extrair insights relevantes a partir de dados tratados e bem modelados. A modelagem foi essencial para que os dados “se conversassem” e possibilitassem análises precisas com DAX e visuais dinâmicos.

---
