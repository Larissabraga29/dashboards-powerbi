# 📘 Referência de Funções — Linguagem M (Power Query)

Este documento reúne todas as funções e comandos utilizados nos desafios práticos de Power Query com **Linguagem M**. Ele serve como um **guia rápido** para revisar, aprender e aplicar essas transformações no meu dia a dia com o Power BI.

## Funções e Comandos da Linguagem M usados nos Exercícios

| Função / Comando                       | Onde foi usado   | O que faz                                                                 |
|----------------------------------------|------------------|---------------------------------------------------------------------------|
| `Csv.Document(...)`                    | Desafio 01       | Lê um arquivo `.csv` do seu computador                                   |
| `File.Contents(...)`                   | Desafio 01       | Localiza o arquivo no seu computador                                     |
| `Table.PromoteHeaders(...)`           | Desafio 01       | Promove a **primeira linha** como cabeçalho da tabela                    |
| `Table.TransformColumnTypes(...)`     | Desafio 01 e 04  | Altera o **tipo de dado** de uma ou mais colunas                         |
| `Int64.Type`                           | Desafio 01       | Define o tipo da coluna como **número inteiro**                          |
| `type text`                            | Desafio 01, 02, 03 | Define o tipo da coluna como **texto**                                  |
| `type number`                          | Desafio 01 e 05  | Define o tipo da coluna como **número decimal**                          |
| `type date`                            | Desafio 04       | Define o tipo da coluna como **data**                                    |
| `Table.RenameColumns(...)`            | Desafio 01       | Renomeia colunas da tabela                                               |
| `Text.Trim(...)`                       | Desafio 02       | Remove **espaços extras** antes e depois de um texto                     |
| `Table.TransformColumns(...)`         | Desafios 02, 04, 05 | Aplica uma transformação a uma ou mais colunas                          |
| `Table.SplitColumn(...)`              | Desafio 03       | Divide uma coluna em **duas ou mais** com base em um delimitador        |
| `Splitter.SplitTextByDelimiter(" - ")`| Desafio 03       | Define que a separação será feita pelo texto `" - "`                    |
| `each ...`                             | Desafios 04 e 05 | Aplica uma **função personalizada** a cada linha da coluna              |
| `Date.FromText(...)`                  | Desafio 04       | Converte um texto em formato data                                        |
| `try ... otherwise null`              | Desafios 04 e 05 | Tenta executar a função; se der erro, retorna `null`                     |
| `Text.Replace(...)`                   | Desafio 05       | Substitui um caractere por outro dentro de um texto                      |
| `Number.FromText(...)`                | Desafio 05       | Converte texto (ex: `"1000.5"`) para número (`1000.5`)                   |
