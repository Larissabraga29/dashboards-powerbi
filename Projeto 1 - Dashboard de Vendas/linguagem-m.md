# Resumo de Linguagem M (Power Query)

## 📌 O que é Linguagem M?

Linguagem M é usada no Power Query para **transformar e limpar os dados**  e é usado detro do power query.  
"M" - MASHUP (Mistura de dados de várias fontes) -- Ela permite que você trate dados **de várias fontes** (Excel, CSV, Banco de Dados, Web etc). 

É uma linguagem **funcional**, baseada em **etapas encadeadas**, onde cada etapa depende da anterior.

---

##  Onde usamos Linguagem M?

✅ Dentro do **Power Query**  
❌ **Não** é usada para cálculos, visuais ou análise final (isso é função do DAX)

**É uma linguagem nativa e principal do POWER QUERY**
---

##  Estrutura Básica da Linguagem M

```m
let
    NomeEtapa1 = EtapaInicial,
    NomeEtapa2 = FunçãoAplicada(NomeEtapa1),
    NomeEtapaFinal = OutraFunção(NomeEtapa2)
in
    NomeEtapaFinal

```

## Explicando:

| Palavra-chave | Função |
|---------------|--------|
| `let`         | Início do bloco onde definimos as etapas |
| `=`           | Atribui o resultado da função a um nome de etapa |
| `in`          | Define qual etapa será o resultado final (retorno da consulta) |

### Prefixos mais comuns da Linguagem M

| Prefixo      | Trabalha com...    | Exemplos de função                      |
|--------------|--------------------|------------------------------------------|
| `Table.`     | Tabelas completas  | `Table.SelectRows`, `Table.Sort`         |
| `List.`      | Listas (1 coluna)  | `List.Count`, `List.Distinct`            |
| `Text.`      | Textos             | `Text.Upper`, `Text.Replace`             |
| `Number.`    | Números            | `Number.Round`, `Number.Abs`             |
| `Date.`      | Datas              | `Date.Year`, `Date.AddDays`              |
| `Record.`    | Registros (linhas) | `Record.FieldValues`, `Record.ToList`    |
| `each`       | Para cada linha    | `each [Nome] <> null`                    |
| `type`       | Tipos de dados     | `type text`, `Int64.Type`, `type date`   |


Palavra-chave	Função
let	Início do bloco onde definimos as etapas
=	Atribui o resultado da função a um nome de etapa
in	Define qual etapa será o resultado final (retorno da consulta)

### Exemplos comuns no dia a dia

| Função                            | O que faz?                                         |
|----------------------------------|----------------------------------------------------|
| `Table.PromoteHeaders`           | Torna a primeira linha o nome das colunas         |
| `Table.TransformColumnTypes`     | Altera o tipo de cada coluna                      |
| `Table.SelectRows`               | Filtra linhas de uma tabela com base em condição  |
| `Text.Upper`, `Text.Lower`       | Converte texto para maiúsculo/minúsculo           |
| `List.Count`                     | Conta quantos itens tem dentro de uma lista       |
| `Date.Year([Data])`              | Extrai o ano de uma data                          |

