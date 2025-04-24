# Estudo de Caso

Trabalhamos com uma base de dados onde cada cliente tem o histórico de compra em 5 campanhas distintas. O objetivo principal foi **avaliar a performance geral das campanhas**, começando pela identificação de **quantos clientes compraram x quantos não compraram**. A partir disso, aprofundamos a análise cruzando com variáveis como **salário, visitas ao site, escolaridade, estado civil e filhos em casa**.

Essa etapa é essencial no marketing porque permite:

- Identificar **o perfil de compra do cliente**
- Segmentar o público com base em **comportamentos reais**
- Direcionar os próximos investimentos com mais precisão


Antes de qualquer análise de marketing, é essencial garantir que a **base de dados esteja estruturada e confiável**. No Power BI, a primeira etapa do projeto foi dedicada à **importação, limpeza e preparação dos dados**. Isso inclui:

- Verificar se os números estão coerentes
- Corrigir formatações (valores, datas, categorias)
- Alterar tipos de dados conforme a necessidade 
- Tratar campos nulos ou inconsistentes

> Etapa crucial para entender, quais gráficos usar, quais variáveis cruzar e como repreentar as informações!



---

## Objetivo do Projeto

Avaliar a **efetividade de campanhas de marketing** com base em:
- Total de compras x não-compras
- Perfil dos clientes que mais consomem
- Variáveis como filhos em casa, escolaridade e estado civil

Esses dados devem ser representados no dashboard em diferentes visões:
- Visão Clientes:
- Visão comportamento:
- Performance das campanhas:
- Padrões por região e PDV:

  
---

# Etapas da Análise



### Modelagem Conceitual da Análise

| Visão de Negócio                                | Visão de Marketing                                              | O que olhar nos Dados                                                |
|--------------------------------------------------|------------------------------------------------------------------|-----------------------------------------------------------------------|
| Entender quem é o público da marca               | Criar campanhas mais direcionadas                                | Escolaridade, Estado Civil, País                                     |
| Aumentar conversão de campanhas                  | Saber quais perfis respondem melhor                              | Comprou x Não Comprou, Faixa Salarial                               |
| Avaliar retorno dos canais (físico x digital)    | Ajustar verba entre canais e melhorar usabilidade do site        | Canais de Compra, Visitas ao Website                                |
| Otimizar orçamento de mídia                      | Segmentar públicos e otimizar criativos                          | Filhos em Casa, Segmentação por Perfil Demográfico                  |
| Testar estratégias promocionais                  | Entender se descontos realmente impactam nas vendas              | Total de Compras com Desconto                                       |


> Foi essencial estruturar uma modelagem conceitual que conectasse as perguntas de negócio com os dados disponíveis. Isso garantiu que a análise tivesse um direcionamento estratégico claro.

## 1. Visão Clientes – Análise Demográfica e de Compras

Essa aba tem como objetivo em compreender o perfil dos consumidores da base e identificar padrões comportamentais e demográficos que pudessem ser relevantes.

Iniciei escolhendo os dados que mais se encaixam com esse objetivo para serem refletidos de forma coerente nos gráficos, como base a ideia foi de **desenhar o retrato do cliente**, observando características como:

| Variável              | Objetivo da Análise                                                                 |
|-----------------------|-------------------------------------------------------------------------------------|
| **Renda**             | Entender o poder de compra dos clientes.                                           |
| **Escolaridade**      | Avaliar o nível de informação para ajustar a linguagem e abordagem das campanhas.  |
| **Estado civil e filhos** | Observar possíveis relações entre estrutura familiar e comportamento de consumo.   |
| **Canais de compra**  | Verificar por onde os clientes compram (loja física ou web).                       |
| **Descontos**         | Analisar o impacto das promoções no volume de compras.                             |


> Essas informações são **fundamentais para o marketing**: Quem são os nossos clientes? Como e onde eles compram? e Quais perfis respondem melhor a promoções?

### Representação Visual
---

O gráfico do tipo **"Cartão"** foi escolhido para representar de forma **simples, direta e limpa** os principais indicadores numéricos.

Já os **gráficos de colunas** foram utilizados para representar a **distribuição dos clientes por categoria**, como:

- **Contagem de ID por Escolaridade**
- **Contagem de ID por Estado Civil**

Essa escolha foi feita porque os gráficos de colunas facilitam a **comparação entre grupos**, deixando claro **qual categoria tem maior representatividade** dentro da base de dados.

Por último, utiizei o gráfico de cartões para o usuário filtre o dashboard inteiro por país, o que é muito poderoso para análises regionais. Ideal pra comparar o perfil dos clientes em diferentes localizações.

---

## Qual o perfil do cliente até o momento?

## **ível superior de escolaridade**
## **solteiro**, o que pode indicar maior autonomia na decisão de compra
## E reside principalmente em **determinados países estratégicos** da operação



Com esses aprendizados em mãos, seguimos para a próxima etapa: analisar o **comportamento de compra**, cruzando esses perfis com hábitos de consumo, canais e valores gastos.

