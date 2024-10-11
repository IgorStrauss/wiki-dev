# Dax

## TREATAS 

A função TREATAS no DAX é usada para aplicar o contexto de filtragem de uma tabela a outra, mesmo que essas tabelas não tenham uma relação direta no modelo de dados. Ela permite mapear colunas entre duas tabelas e aplicar um filtro, de forma que se comportem como se estivessem relacionadas.

Essa função é particularmente útil em cenários em que você quer utilizar uma tabela para influenciar o comportamento de outra tabela, sem precisar criar relações físicas no modelo de dados, evitando a necessidade de relacionamentos complexos ou indesejados.


TREATAS pega os valores da primeira tabela ou coluna e os projeta sobre uma ou mais colunas de destino de outra tabela, como se estivesse filtrando essas colunas com base nos valores projetados.


Exemplo Simples:
Imagine que você tem as seguintes tabelas:
Tabela Calendário com uma coluna Data.
Tabela Fato com uma coluna DataFato que não está diretamente relacionada com a tabela calendário.
Você deseja aplicar os filtros de data da Tabela Calendário na Tabela Fato sem criar um relacionamento físico entre elas.
Aqui está como TREATAS funcionaria:
 
    CALCULATE(
        SUM('TabelaFato'[Valor]),
        TREATAS(
            VALUES('TabelaCalendario'[Data]), 
            'TabelaFato'[DataFato]
        )
    )

Aplicação

TREATAS é frequentemente usada para:

- Aplicar filtros entre tabelas que não possuem relacionamento direto.

- Implementar filtros de cenários ou simulações com tabelas desconectadas (por exemplo, em painéis de análise de cenários).

- Evitar relacionamentos físicos que podem complicar o modelo de dados.

Ao usar TREATAS, você pode filtrar dados dinamicamente, com flexibilidade e sem precisar alterar a estrutura do modelo, permitindo uma abordagem mais modular e controlada para análises complexas.


## CALCULATE

A função CALCULATE é uma das mais poderosas e essenciais no DAX. Ela é usada para modificar o contexto de filtro de uma medida ou expressão, permitindo que você calcule valores com base em condições ou filtros específicos. O principal papel da CALCULATE é mudar o contexto de avaliação de uma expressão ao aplicar um ou mais filtros.

    CALCULATE(<expressão>, <filtro1>, <filtro2>, ...)


- `expressão`: A expressão a ser avaliada (geralmente uma medida ou uma agregação como SUM, COUNT, etc.).
- `filtro1`, `filtro2`, ...: Um ou mais filtros opcionais que alteram o contexto da expressão.

#### Como Funciona

A CALCULATE funciona em dois passos:

Avaliação da expressão: Primeiro, a expressão que você deseja calcular é avaliada no contexto atual.

Aplicação de filtros: Em seguida, os filtros adicionais especificados na função são aplicados, alterando o contexto de filtro no qual a expressão é avaliada.

Essa mudança de contexto permite a criação de métricas complexas, como cálculos condicionais ou cálculos com base em períodos de tempo específicos.
Exemplo de Uso

Vamos supor que temos uma tabela chamada Vendas com as seguintes colunas:

- ValorVenda: O valor de cada venda.
- ProdutoID: O ID do produto vendido.
- Região: A região onde a venda foi feita.

#### Exemplo Básico

Para calcular a soma total das vendas, você pode usar a função SUM diretamente:

    TotalVendas = SUM(Vendas[ValorVenda])

Agora, se você quiser calcular a soma das vendas apenas para uma região específica, digamos "Sul", a função CALCULATE pode ser usada para modificar o contexto:

    TotalVendasSul = CALCULATE(
        SUM(Vendas[ValorVenda]),
        Vendas[Região] = "Sul"
    )

Neste exemplo:

SUM(Vendas[ValorVenda]) calcula o valor total das vendas.
Vendas[Região] = "Sul" é um filtro aplicado pela CALCULATE que limita o cálculo apenas às vendas da região "Sul".

Resultado: A medida TotalVendasSul retorna a soma dos valores de vendas para a região Sul, enquanto outras regiões são ignoradas.

Exemplo Com Múltiplos Filtros

A CALCULATE também suporta a aplicação de múltiplos filtros. Suponha que você queira calcular a soma das vendas para a região "Sul" e para um determinado ProdutoID:

    VendasSulProduto101 = CALCULATE(
        SUM(Vendas[ValorVenda]),
        Vendas[Região] = "Sul",
        Vendas[ProdutoID] = 101
    )

Neste caso, a CALCULATE filtra os dados para a região "Sul" e para o ProdutoID 101 simultaneamente, retornando a soma das vendas para esses critérios específicos.


## USERELATIONSHIP 

A função USERELATIONSHIP no DAX é usada para ativar um relacionamento inativo entre duas tabelas no modelo de dados, permitindo que você controle qual relacionamento é utilizado em um cálculo específico. Isso é útil em modelos de dados onde múltiplos relacionamentos entre as mesmas tabelas existem, mas apenas um relacionamento pode ser ativo por padrão.

Em muitos casos, o modelo de dados contém mais de um relacionamento entre tabelas. Por exemplo, uma tabela de Fato de Vendas pode se relacionar com uma Dimensão de Data tanto pela Data de Venda quanto pela Data de Envio. No entanto, o Power BI ou o Analysis Services permite que apenas um relacionamento seja o principal. A função USERELATIONSHIP permite ativar um relacionamento inativo quando você deseja que ele seja considerado em uma medida ou cálculo.


    USERELATIONSHIP(<Coluna1>, <Coluna2>)

`Coluna1`: A coluna da primeira tabela, correspondente ao relacionamento que deseja ativar.
`Coluna2`: A coluna da segunda tabela que será usada no relacionamento.

A função USERELATIONSHIP não modifica o relacionamento de forma permanente no modelo, mas apenas para o contexto da medida ou expressão em que é utilizada.

Exemplo de Uso

Suponha que você tem as seguintes tabelas no seu modelo:

- FatoVendas: contém informações sobre vendas, incluindo as colunas DataVenda e DataEnvio.
- DimensãoData: uma tabela de datas que contém todas as datas do calendário.

No modelo, existe um relacionamento ativo entre FatoVendas[DataVenda] e DimensãoData[Data], mas também há um relacionamento inativo entre FatoVendas[DataEnvio] e DimensãoData[Data].

Exemplo: Usando o Relacionamento Ativo (Data de Venda)

Para calcular a soma de vendas por Data de Venda (o relacionamento ativo), você pode usar uma medida simples como:

    TotalVendas = SUM(FatoVendas[ValorVenda])

Exemplo: Usando o Relacionamento Inativo (Data de Envio)

Agora, se você quiser calcular as vendas com base na Data de Envio (o relacionamento inativo), você precisa ativar esse relacionamento com USERELATIONSHIP dentro de uma função como CALCULATE:

    TotalVendasPorEnvio = CALCULATE(
        SUM(FatoVendas[ValorVenda]),
        USERELATIONSHIP(FatoVendas[DataEnvio], DimensãoData[Data])
    )

Neste exemplo:

- SUM(FatoVendas[ValorVenda]) calcula o total das vendas.

- USERELATIONSHIP(FatoVendas[DataEnvio], DimensãoData[Data]) ativa temporariamente o relacionamento entre a Data de Envio e a Data na tabela de dimensões, permitindo que o cálculo considere esse relacionamento.

Resultado: Agora, a medida TotalVendasPorEnvio retorna a soma das vendas com base nas datas de envio, em vez de nas datas de venda, sem precisar alterar o relacionamento padrão no modelo.

#### Cenários Comuns de Uso

**Múltiplas Datas Relacionadas**: É comum ter múltiplas colunas de data em uma tabela de fato, como Data de Venda, Data de Envio, e Data de Faturamento. A USERELATIONSHIP permite que você crie medidas diferentes que usem essas várias datas sem alterar o relacionamento principal.

**Análises Comparativas**: A função pode ser útil para análises onde se deseja comparar diferentes datas ou eventos relacionados. Por exemplo, comparar vendas por Data de Venda e Data de Envio lado a lado em um relatório.

**Relatórios Temporais Avançados**: Com USERELATIONSHIP, você pode criar cálculos temporais mais complexos, utilizando diferentes colunas de data para entender o impacto de eventos ao longo do tempo, como o tempo entre venda e envio.

