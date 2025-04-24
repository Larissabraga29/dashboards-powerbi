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

## 2. Visão Comportamento – Gasto e Estrutura Familiar

O objetivo foi entender **como os clientes se comportam em relação ao gasto** e **quais características impactam esse comportamento**. Saímos do “quem é o cliente” para observar **como ele age na hora de comprar**.

As características pessoais e contextos familiares influenciam na forma e no valor com que os clientes compram?

Para investigar se o número de filhos influencia o valor total gasto pelos clientes, criamos um **gráfico de barras com:**

- **Eixo X**: `Filhos em Casa`
- **Eixo Y**: `Precisa mostrar o total gasto com cada categoria`

  Para isso, através do power query criei uma **nova medida** com o nome de `TotalGasto`, essencial para consolidar todas as despesas de forma única.

  #### Fórmula DAX utilizada:
```DAX
TotalGasto = 
    SUMX(
        'BaseClientes',
        'BaseClientes'[Alimentos] +
        'BaseClientes'[Brinquedos] +
        'BaseClientes'[Eletrônicos] +
        'BaseClientes'[Casa] +
        'BaseClientes'[Roupas]
    )

```

> Essa medida tornou possível cruzar o valor total gasto com outras variáveis como número de filhos em casa, estado civil e escolaridade, revelando padrões de comportamento e perfis de consumo.


Além dos gráficos de barras, utilizei um gráfico tipo **Treemap (árvore de segmentação)** para visualizar de forma hierárquica o total gasto por categoria combinando:

- **Filhos em Casa**
- **Estado Civil**
- **Escolaridade**

> A visualização permite entender com profundidade **como diferentes combinações de perfil impactam o valor gasto**.


**Gráfico de Dispersão** foi relacionado com o `TotalGasto` com a `Escolaridade` dos clientes.

- Foi possível observar que **clientes com ensino superior e pós-graduação** não apenas têm maior média de gasto, mas também maior **variação** — o que pode indicar **potenciais clusters de alto valor** para campanhas mais premium.


### A **presença de filhos impacta de forma negativa no valor total gasto**.




## 3. Visão Performance das Campanhas 

Entender **a efetividade das 5 campanhas de marketing realizadas**. A ideia foi sair da análise de perfil e comportamento e passar a avaliar **o resultado direto das ações de mídia**: quem converteu, quando e quais perfis foram mais impactados.

---

### O que foi analisado

- **Número de clientes que compraram em pelo menos uma campanha**
- **Distribuição entre comprou x não comprou**
- **Impacto do perfil do cliente nas compras (ex: escolaridade, filhos, estado civil)**
- **Correlação entre visitas ao site e conversão**
- **Perfis mais sensíveis às campanhas**

---

###  Gráfico de Pizza – Comprou x Não Comprou

Na base original, a coluna `Comprou` utilizava os valores **"1" para Sim** e **"0" para Não**, representando se o cliente comprou em pelo menos uma das campanhas.

Para facilitar a leitura e tornar o gráfico mais intuitivo para o usuário final, fiz um ajuste no **Power Query**, substituindo os valores:

- `"1"` → `"Sim"`
- `"0"` → `"Não"`

> Essa transformação garantiu que o gráfico de pizza representasse corretamente a proporção de clientes que **compraram ou não**, usando uma linguagem mais acessível.

---

### Gráficos

#### Gráfico de Pizza – Qual foi o resultado das campanhas?

- Mostra a proporção entre clientes que compraram e os que não compraram.

#### Gráfico de Barras – Média de Salário Anual x Resultado das campanhas

- Cruzamos a variável `Comprou` com `Filhos em Casa`.
- O objetivo foi identificar se a estrutura familiar tem impacto na conversão.
- Resultado: **clientes sem filhos** converteram muito mais que os demais.

#### Tabela Cruzada – Escolaridade x Estado Civil x País

- Essa matriz permite aprofundar ainda mais o perfil dos clientes que compraram.
- Mostra como **combinações de atributos** influenciam a resposta à campanha.
- Ex: Solteiros com curso superior são maioria entre os que compraram.

> Essa visão é muito útil para planejamento de mídia e definição de **clusters de audiência**.

---

## 4. Visão Padrões de Compra por Pontos de Venda

Nesta aba, o foco foi entender **onde estão concentradas as vendas** e quais categorias de produto se destacam em cada região. A análise foi feita com base na variável `País`, representando os diferentes **mercados atendidos pela marca**.

###  Gráfico de Colunas Agrupadas com Linha – Gasto por Categoria + Volume de Clientes

Esse gráfico foi construído com o objetivo de cruzar dois tipos de informação:

- **Colunas (eixo primário)**: mostram o total de gastos por país em cada categoria de produto:
  - Alimentos
  - Brinquedos
  - Eletrônicos
  - Móveis
  - Utilidades
  - Vestuário

- **Linha (eixo secundário)**: representa a **quantidade de clientes por país** (Contagem de ID)

> A escolha desse gráfico foi estratégica para visualizar **volume financeiro x volume de clientes** — ou seja, entender não só onde se gasta mais, mas **onde há maior densidade de compradores**.

---

### O que esse gráfico revela?

- **Estados Unidos** aparece com **maior volume de gasto total e número de clientes**, sendo um mercado prioritário.
- **Espanha e Chile** também se destacam com boas combinações de volume e variedade de categorias.
- **Brasil, Portugal e Alemanha** têm menor expressão na base, o que pode indicar **baixa penetração de mercado** ou **menos presença de campanha/publicidade local**.

---

Essa visualização permite tomar **decisões geográficas mais informadas**, como:

- Direcionar campanhas específicas para regiões com maior potencial
- Otimizar estoques e logística baseando-se na **demanda regional por categoria**

> Essa análise pode ajudar a compreender “**Onde estão nossos clientes mais lucrativos e o que eles mais compram?**”

Com base nesse gráfico, conseguimos priorizar ações por região, melhorar o uso de verba por praça e trabalhar o mix de produtos conforme o comportamento local.

---

---

## Conclusão

Ao longo deste estudo, foi possível construir um dashboard completo, estruturado em quatro visões principais, que permitiu:

- **Compreender o perfil demográfico dos clientes**
- **Analisar comportamentos de compra e padrões por perfil**
- **Avaliar a performance das campanhas de marketing**
- **Identificar oportunidades regionais por ponto de venda**

Mais do que visualizar os dados, esse processo me permitiu aplicar **conceitos de análise de dados orientada ao marketing**, desde a limpeza da base até a construção de insights acionáveis.

> O resultado final foi a criação de uma ferramenta estratégica para o time de mídia e marketing, capaz de apoiar decisões mais inteligentes, segmentadas e com maior potencial de conversão.

Esse foi um exercício prático de como **dados bem estruturados, combinados com boas perguntas de negócio**, geram valor real para a marca.



