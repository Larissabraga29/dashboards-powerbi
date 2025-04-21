# Desafios Práticos – Power Query & Linguagem M

Este espaço é dedicado à prática da **Linguagem M** no Power BI, usada dentro do Power Query para transformar, limpar e preparar dados antes da análise. Aqui você encontra exercícios práticos comentados, com códigos, explicações e aprendizados.

---

## Sumário de Exercícios

| Desafio | Título |
|---------|--------|
| 01 | Renomear coluna `123Nome` para `Nome` |
| 02 | *(em breve)* Remover espaços extras de texto com `Text.Trim` |
| 03 | *(em breve)* Separar `Cidade_Estado` em duas colunas |
| 04 | *(em breve)* Corrigir formatos e transformar `DataNasc` em data válida |
| 05 | *(em breve)* Tratar valores com vírgula, ponto e símbolo R$ em `ValorVenda` |

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


