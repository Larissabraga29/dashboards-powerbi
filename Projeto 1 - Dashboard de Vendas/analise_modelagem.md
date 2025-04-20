
Este documento detalha o processo completo de construção do dashboard "Vendas, Custos, Margem de Lucro e KPI", desenvolvido como parte dos meus estudos em Análise de Dados com Power BI.

Etapas do Projeto

1. O objetivo principal era responder às seguintes perguntas sobre o negócio:

1. Qual foi o total valor de venda considerando cada modo de envio dos pedidos?

2. Quais mercados tiveram o maior custo médio de envio dos produtos vendidos?
   
3. Considere que o lucro é equivalente a: valor de venda - custo envio. Qual categoria de produto apresentou maior lucro médio.

4. A empresa alcançou a média de R$350 em valor de venda no mês de abril/2014?

5. Qual foi o comportamento da margem de lucro ao longo do tempo?


2. Escolha dos Gráficos 

Para cada pergunta, entendi qual gráfico era mais adequado para visualização:

Pizza (Rosca): Exibir lucro médio por tipo de produto

Cascata: Mostrar o total de vendas por modo de envio

Indicador (KPI): Indicar se a média de vendas em abril/2014 atingiu a meta de R$350

Treemap: Apresentar o custo médio de envio por região

Gráfico de Linha: Analisar o comportamento da margem de lucro ao longo do tempo



3. Importação dos Dados

Importei as seguintes tabelas no Power BI Desktop (como CSV):

Clientes, Pedidos, Produtos e Vendas.

Durante a análise inicial, detectei alguns problemas de integridade e padronização, como:

. Colunas com tipos de dados incorretos (ex: texto no lugar de número)

. Dados duplicados

. Campos com nomes diferentes dificultando o relacionamento

Esses problemas dificultariam a criação de relacionamentos consistentes e a análise correta dos indicadores, importando da maneira original os resultados nos gráficos seriam inconsistentes.



-----------------------------------------------------  Início de Limpeza e Ajustes com Power Query  -----------------------------------------------------------------



A etapa de tratamento de dados foi feita no Power Query, utilizando a linguagem M. Algumas ações realizadas:

- Remoção de valores duplicados nas tabelas

- Conversão de tipos de dados, como datas e valores numéricos

- Padronização de nomes de colunas para facilitar a criação de relacionamentos

- Separação de colunas compostas, quando necessário



= Dados limpos e prontos para análise!




5. Criação de Métricas com DAX


Utilizei a linguagem DAX (Data Analysis Expressions- Uma versão mais "Avançada do BI") para calcular métricas personalizadas, como:

- **Lucro:** Valor Venda - Custo Envio                                     Fórmula:  (Lucro = Vendas[Valor Venda] - Vendas[Custo Envio])
- **Margem de Lucro:** (Lucro / Valor Venda) * 100                         Fórmula:  (MargemLucro = ROUND(DIVIDE(Vendas[Lucro], Vendas[Valor Venda]) *100, 2)

  
Essas medidas permitiram análises mais detalhadas e responderam diretamente às perguntas de negócio.



6. Modelagem de Dados

Realizei os relacionamentos entre as tabelas respeitando a cardinalidade correta:

- **Produtos (1) : (N) Vendas**  
- **Clientes (1) : (N) Vendas**

Essa modelagem garantiu a integridade entre as informações e permitiu cruzar dados de diferentes fontes com precisão.



 7. Análise Final

Depois de limpar os dados, organizar as tabelas e criar as métricas com DAX, consegui montar um dashboard que realmente responde às perguntas do negócio de forma visual e simples de entender.
Esse projeto foi essencial pra eu sair do básico e colocar a mão na massa! Consegui aplicar tudo o que venho estudando na teoria — desde o que é BI, linguagem M, estrutura de dados, até como organizar as informações pra que o Power BI consiga entender e conectar tudo direitinho.

**Ao longo do caminho, aprendi a**:

Limpar e transformar os dados (tirar duplicados, arrumar formatos, padronizar nomes…)

Relacionar tabelas do jeito certo, respeitando a cardinalidade (um para muitos, lembra? rs)

Criar indicadores importantes com DAX, como lucro e margem de lucro

Pensar no usuário final, deixando tudo visual e fácil de navegar

Foi um baita exercício de prática mesmo: errei, voltei, revisei os relacionamentos, testei fórmulas e no fim consegui entregar algo funcional. Tudo isso com base nos resumos que fui fazendo pra entender melhor os conceitos.
