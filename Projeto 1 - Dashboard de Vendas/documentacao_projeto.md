
Este documento detalha o processo completo de construção do dashboard **"Vendas, Custos, Margem de Lucro e KPI"**, desenvolvido como parte dos meus estudos em Análise de Dados com Power BI.

---

 ## Etapas do Projeto

O objetivo principal era responder às seguintes **perguntas de negócio**:

1.  Qual foi o valor total de vendas por modo de envio?
2.  Quais mercados tiveram o maior custo médio de envio?
3.  Qual categoria de produto apresentou maior lucro médio?
4.  A empresa alcançou a média de **R$350** em vendas no mês de **abril/2014**?
5.  Qual foi o comportamento da margem de lucro ao longo do tempo?


## Escolha dos Gráficos

Para cada pergunta, entendi qual gráfico era mais adequado para visualização:

| Visual        | Objetivo                                                |
|---------------|----------------------------------------------------------|
| Rosca (Pizza) | Exibir **lucro médio por tipo de produto**              |
| Cascata       | Mostrar o **total de vendas por modo de envio**         |
| KPI           | Verificar se a média de vendas de abril/2014 bateu R$350 |
| Treemap       | Exibir **custo médio de envio por região**              |
| Linha         | Analisar a **margem de lucro ao longo do tempo**        |



## Importação dos Dados

Importei as seguintes tabelas no Power BI Desktop (como CSV):

- `Clientes`
- `Pedidos`
- `Produtos`
- `Vendas`


Durante a análise inicial, detectei alguns problemas de qualidade dos dados:

- Colunas com **tipos incorretos** (ex: texto no lugar de número)
- **Dados duplicados**
- **Nomes diferentes** dificultando os relacionamentos

Esses problemas poderiam prejudicar a análise e trazer resultados incorretos.

---

## Limpeza e Ajustes com Power Query (Linguagem M)


Usei o Power Query para tratar os dados utilizando **Linguagem M**. Abaixo algumas ações realizadas:

- Remoção de **valores duplicados**
- Conversão correta de **tipos de dados**
- **Padronização dos nomes** das colunas
- Separação de colunas compostas


✅ **Resultado:** Dados limpos e prontos para análise!


## Criação de Métricas com DAX


Apliquei **DAX (Data Analysis Expressions)** para calcular medidas personalizadas:

 **Lucro:**  
  `Lucro = Vendas[Valor Venda] - Vendas[Custo Envio]`

- **Margem de Lucro (%):**  
  `MargemLucro = ROUND(DIVIDE([Lucro], Vendas[Valor Venda]) * 100, 2)`

Essas medidas foram essenciais para responder às perguntas do negócio.



## Modelagem de Dados

Relacionei as tabelas respeitando a **cardinalidade** correta:

| Relacionamento             | Tipo           |
|----------------------------|----------------|
| Produtos → Vendas          | 1 : N (um para muitos) |
| Clientes → Vendas          | 1 : N (um para muitos) |

Isso garantiu a integridade dos dados e permitiu análises cruzadas.

---


## Análise Final

Depois de limpar os dados, organizar as tabelas e criar as métricas com DAX, consegui montar um dashboard que realmente responde às perguntas do negócio de forma visual e simples de entender.
Esse projeto foi essencial pra sair do básico e colocar a mão na massa! Consegui aplicar tudo o que venho estudando na teoria — desde o que é BI, linguagem M, estrutura de dados, até como organizar as informações pra que o Power BI consiga entender e conectar tudo direitinho.

**Ao longo do caminho, aprendi a**:

- Limpeza de dados (remover duplicados, corrigir tipos, padronizar colunas)
- Modelagem (entender relações e cardinalidade)
- Criação de métricas com DAX
- Escolha estratégica dos gráficos para responder perguntas reais
- Pensar no usuário final e na clareza da visualização

Foi um baita exercício de prática!  
Errei, revisei, testei fórmulas e no final entreguei algo funcional. Tudo isso com base nos **resumos que fui construindo ao longo dos estudos** — e esse projeto consolidou tudo que aprendi até aqui.

