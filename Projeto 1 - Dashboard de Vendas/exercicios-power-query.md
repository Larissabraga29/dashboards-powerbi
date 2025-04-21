# Desafios Práticos – Power Query & Linguagem M

Este espaço é dedicado à prática da **Linguagem M** no Power BI, usada dentro do Power Query para transformar, limpar e preparar dados antes da análise. Aqui você encontra exercícios práticos comentados, com códigos, explicações e aprendizados.

---

## Sumário de Exercícios

| Desafio | Título |
|---------|--------|
| 01 | Renomear coluna `123Nome` para `Nome` |
| 02 | Remover espaços extras de texto com `Text.Trim` |
| 03 | Separar `Cidade_Estado` em duas colunas |
| 04 | Corrigir formatos e transformar `DataNasc` em data válida |
| 05 | Tratar valores com vírgula, ponto e símbolo R$ em `ValorVenda` |

### 1. Renomear a coluna `123Nome` para `Nome`

> Para essa etapa, adicionei uma nova linha no Editor Avançado com a função:
> 
> `#"Colunas Renomeadas" = Table.RenameColumns(#"Tipo Alterado", {{"123Nome", "Nome"}})`  
> 
> Essa função cria uma **nova etapa** no código e altera o nome da coluna `123Nome` para `Nome`.

---

### 💻 Código completo:

```m
#"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true])

#"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos", {
    {"ID", Int64.Type}, 
    {"123Nome", type text}, 
    {"DataNasc", type text}, 
    {"Cidade_Estado", type text}, 
    {"ValorVenda", type number}
})

#"Colunas Renomeadas" = Table.RenameColumns(#"Tipo Alterado", {{"123Nome", "Nome"}})

in
    #"Colunas Renomeadas"

```

###  Explicação:
A função Table.RenameColumns é utilizada para alterar o nome de colunas em uma tabela.
Ela recebe dois argumentos:

1. A etapa anterior (no caso, "Tipo Alterado")

2. Um par { "NomeAtual", "NovoNome" }

Finalizei a consulta com o comando in, que indica que o resultado final exibido será a tabela da etapa "Colunas Renomeadas".

## Desafio 02 – Remover espaços extras com `Text.Trim`

---

###  Objetivo

Remover espaços em branco indesejados no início ou fim do conteúdo da coluna `Nome`.

Na base bruta, alguns nomes vinham com espaços antes ou depois do texto (ex: `"   Henrique"`), o que poderia impactar comparações, agrupamentos ou visualização no dashboard.

---

###  Solução aplicada

Utilizei a função `Text.Trim` dentro de `Table.TransformColumns` para aplicar essa limpeza apenas na coluna `Nome`.

---

###  Código aplicado no Editor Avançado

```m
#"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),

#"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos", {
    {"ID", Int64.Type},
    {"123Nome", type text},
    {"DataNasc", type text},
    {"Cidade_Estado", type text},
    {"ValorVenda", type number}
}),

#"Colunas Renomeadas" = Table.RenameColumns(#"Tipo Alterado", {{"123Nome", "Nome"}}),

#"Nome Sem Espaços" = Table.TransformColumns(#"Colunas Renomeadas", {{"Nome", Text.Trim}})

in
    #"Nome Sem Espaços"

```

## Desafio 03 – Separar `Cidade_Estado` em duas colunas

---

### Objetivo

Transformar a coluna `Cidade_Estado`, que contém valores como `"SP - São Paulo"` em **duas colunas distintas**:

- `UF` (ex: SP, RJ, MG...)
- `Cidade` (ex: São Paulo, Rio, Belo Horizonte...)

Isso facilita segmentações regionais, cruzamento com tabelas externas e visualizações.

---

###  Solução aplicada

Utilizei a função `Table.SplitColumn`, combinada com `Splitter.SplitTextByDelimiter`, para dividir a coluna com base no delimitador `" - "`.

---

### 💻 Código aplicado no Editor Avançado

```m
let
    Fonte = Csv.Document(File.Contents("caminho/do/arquivo.csv"), [Delimiter=",", Columns=5, Encoding=65001, QuoteStyle=QuoteStyle.None]),

    #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),

    #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos", {
        {"ID", Int64.Type},
        {"123Nome", type text},
        {"DataNasc", type text},
        {"Cidade_Estado", type text},
        {"ValorVenda", type number}
    }),

    #"Colunas Renomeadas" = Table.RenameColumns(#"Tipo Alterado", {{"123Nome", "Nome"}}

```

 **Aprendi a usar** no código e altera o nome da coluna `table.SplitColumn` para dividir uma coluna existente.
 Que o Splitter.SplitTextByDelimiter (" - ") define onde a separação acontece 



## Desafio 04 – Corrigir formatos e transformar `DataNasc` em data válida

---

### Objetivo

Ajustar a coluna `DataNasc`, que contém formatos misturados como:

- `01/01/1990`
- `1992-02-15`
- `04/1993`
- `1990`

Transformando-a em um **formato de data válido** no Power BI. Isso é essencial para análises temporais, filtros por período, agrupamentos por mês, ano etc.

---

### 💻 Código aplicado no Editor Avançado

```m
#"Data Corrigida" = Table.TransformColumns(#"Cidade Separada", {
    {"DataNasc", each try Date.FromText(_) otherwise null, type date}
})
in
    #"Data Corrigida"

```

**Aprendi a usar** `Table.TransformColumns` que aplica uma transformação a uma ou mais colunas da tabela.
`each try ... otherwise ...	` que tenta aplicar a conversão (com try). Se não conseguir, retorna null
`Date.FromText(_)` que converte um valor de texto para o tipo Data
`type date	` que define que a nova coluna resultante será reconhecida como Data


##  Desafio 05 – Tratar valores com vírgula, ponto e símbolo R$ em `ValorVenda`

---

###  Objetivo

Tratar a coluna `ValorVenda`, que apresenta valores com formatos inconsistentes como:

- `R$ 1.000,5`
- `750`
- `30000`

Esses valores não são lidos como número corretamente, o que inviabiliza somas, médias e outras análises.

---

### Solução aplicada com Linguagem M

Primeiro, transformamos a coluna para texto (caso ainda esteja como número):

```m
#"Valor como Texto" = Table.TransformColumnTypes(#"Data Corrigida", {
    {"ValorVenda", type text}})


```

Depois, limpamos e convertimos os valores com:

```m
#"Valor Corrigido" = Table.TransformColumns(#"Valor como Texto", {
    {"ValorVenda", each try Number.FromText(
        Text.Replace(Text.Replace(Text.Replace(_, "R$", ""), ".", ""), ",", ".")
    ) otherwise null, type number}})

```
E o bloco final do código:

```m
in
    #"Valor Corrigido"

```

